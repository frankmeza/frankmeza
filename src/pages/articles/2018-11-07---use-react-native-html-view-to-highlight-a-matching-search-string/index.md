---
title: Use React Native HTMLView to highlight a matching search string
date: "2018-11-08T09:00:00.0Z"
layout: post
draft: false
path: "/posts/use-react-native-htmlview-to-hightlight-a-matching-search-string"
category: "web development"
tags:
  - "react native"
  - "typescript"
  - "HTMLView"
description: "Use ReactNative HTMLView to highlight a matching search string."
---

`$ yarn install react-native-htmlview`


## The codes

```typescript
import * as React from "react"

const SEARCH_PROMPT: string = "Enter pet's name or number"
const SEARCH: string = "Search for pet"

export interface PetSearchModalProps {
    readonly pets: PetsList
    readonly closeModal: () => void
    readonly onClick: (petName: string, id: string) => void
}

export interface PetSearchModalState {
    readonly searchString: string
    readonly formattedPetsAndIds: ReadonlyArray<string>
}

export default class PetSearchModal extends React.Component<
    PetSearchModalProps,
    PetSearchModalState
> {
    constructor(props: PetSearchModalProps) {
        super(props)
        this.renderHeader = this.renderHeader.bind(this)
        this.renderSearchBar = this.renderSearchBar.bind(this)
        this.handleSelectPet = this.handleSelectPet.bind(this)
        this.renderPet = this.renderPet.bind(this)
        this.renderFormattedPets = this.renderFormattedPets.bind(this)

        this.state = {
            searchString: "",
            formattedPetsAndIds: [""],
        }
    }

    componentDidMount(): void {
        const { pets } = this.props
        const formattedPetsAndIds: ReadonlyArray<
            string
        > = pets.petsList.map(
            (p: Pet) => p.formattedNameAndId,
        )

        this.setState({ formattedPetsAndIds })
    }

    renderHeader(): JSX.Element {
        const { closeModal } = this.props

        return (
            <View>
                <Text>{SEARCH}</Text>
                <TouchableOpacity
                    onPress={closeModal}>
                    <Icon
                        name="times"
                        size={moderateScale(18)} />
                </TouchableOpacity>
            </View>
        )
    }

    renderSearchBar(): JSX.Element {
        return (
            <View>
                <Text>{SEARCH_PROMPT}</Text>
                <TextInput
                    autoFocus={true}
                    value={this.state.searchString}
                    onChangeText={(searchString: string) =>
                        this.setState({ searchString })
                    }
                />
            </View>
        )
    }

    handleSelectPet(p: Pet): void {
        const { closeModal, onClick } = this.props
        onClick(p.name, p.id)
        closeModal()
    }

    renderHTMLText(Petstring: string): JSX.Element {
        const { searchString } = this.state
        const htmlFormattedString: string = makeMatchingStringBold(Petstring, searchString)

        return (
            <HTMLView
                value={htmlFormattedString}
                addLineBreaks={false}
                stylesheet={htmlStyle}
            />
        )
    }

    renderPet(pet: Pet, i: number): JSX.Element {
        return (
            <View key={i}>
                <TouchableOpacity onPress={() => this.handleSelectPet(pet)}>
                    {this.renderHTMLText(pet.formattedNameAndId)}
                </TouchableOpacity>
            </View>
        )
    }

    renderFormattedPets(): ReadonlyArray<JSX.Element> {
        const { formattedPetsAndIds, searchString: s } = this.state
        const { pets } = this.props

        return formattedPetsAndIds.map(
            (petInfo: string, index: number) => {
                const Pet: Pet | undefined = getPet(
                    pets,
                    petInfo,
                )

            return Pet && containsSearchString(Pet.formattedNameAndId, s)
                ? this.renderPet(Pet, index)
                : <View key={index} />
        })
    }

    render(): JSX.Element {
        return (
            <React.Modal
                animationType="slide"
                transparent={true}
                onRequestClose={() => {
                    return true
                }}
                visible={true}>
                <View>
                    <View>
                        {this.renderHeader()}
                        {this.renderSearchBar()}
                        <ScrollView
                            keyboardShouldPersistTaps="always"
                        >
                            {this.renderFormattedPets()}
                        </ScrollView>
                    </View>
                </View>
            </Modal>
        )
    }
}

// utils

 export const getPet = (
    Pets: PetsList,
    formattedString: string,
): Pet | undefined => {
    const { PetsList } = Pets
    const Pet: Pet | undefined = PetsList.find(
        (p: Pet) => p.formattedNameAndId === formattedString,
    )
    return Pet
}

export const containsSearchString = (
    PetNameAndId: string,
    filterString: string,
): boolean => {
    const filter: string = filterString.toLowerCase()
    const Pet: string = PetNameAndId.toLowerCase()
    return Pet.includes(filter)
}

 export const makeMatchingStringBold = (
    petName: string,
    search: string,
): string => {
    if (search === "") {
        return `<p>${petName}</p>`
    }

    const searchString = new RegExp(`(${search})`, "gi")
    const petNameSplitOnSearch: string = petName.split(search)

    const finalOutput: string = petNameSplitOnSearch.map(char => {
        return char.toLowerCase() === search.toLowerCase()
            ? `<p><b>${char}</b></p>`
            : `<p>${char}</p>`
    }).join("")

    return `<span>${finalOutput}</span>`
}
```

