# SRP
https://jaapniks.github.io/SRP/


# Framer X SRP Documentatie
Voor dit Studie Regie Punt ben ik mij gaan verdiepen in hoe de basis van React werkt en hoe dit te gebruiken binnen de nieuwe tool Framer X. Als eindopdracht was het herontwerpen van het programma van de Minor Web Dev door gebruik te maken van components gemaakt in Framer X door middel van React. 

## [Design + Code Framer X](https://designcode.io/framer-x-course)
In de Framer X cursus van Design + Code gemaakt door de oprichter Meng To. De eerste lessen focussen zich op hoe je kan ontwerpen in de tool en snel prototypes kan maken aan de hand van de interactieve opties die Framer X bied. De React components tijdens de cursus worden onder andere gemaakt door gebruik te maken van [Styled Components](https://www.styled-components.com/). Styled Components worden onder andere gebruikt door bedrijven zoals Atlassain en Doordash. Styled Components maakt het makkelijker om components te stylen. 

```
// Styled components moeten boven aan de pagina worden ingeladen

import styled from 'styled-components'

// Voor het stylen van components door Styled Components te gebruiken schrijf je styled.<html tag>``

const Button = styled.button`
  background: transparent;
  border-radius: 3px;
  border: 2px solid palevioletred;
  color: palevioletred;
  margin: 0 1em;
  padding: 0.25em 1em;
`
```

Later in de cursus maak je gebruik van API's binnen Framer X en maak je een dynamisch code component.

<Voorbeeld 2 met Grid Component>

## [Framer ES6 / React Guide](https://paper.dropbox.com/doc/Framer-ES6-React-Guide--Ad7dZMVaHcdcwtuPFVA2QdYcAg-Th7joG9fFSSiyZgOFYqj6)
Deze ES6 / React guide voor Framer is geschreven door 1 van de oprichters van Framer met als doel om de basis rondom React te kunnen leren om basis prototypes te kunnen maken. Alle beginners onderwerpen zoals imports, exports, variables en functions worden. Zo moet bij elk jsx of tsx React worden geïmporteerd aan het begin: 

```
import * as React from "react"
```

Om onderdelen te kunnen gebruiken de Framer API zoals een Frame of een Stack moeten die ook geïmporteerd worden in het project met de volgende regel code:

```
import { Frame, Stack } from "framer"
```

React is populair vanwege het gebruik van components. Components maak het mogelijk om een soort van je eigen HTML tags te kunnen schrijven en die opnieuw te kunnen gebruiken. Hier door hoef je minder code te schrijven omdat je stukken code die je eerder hebt geschreven kan hergebruiken op andere plekken. In de manier van opschrijven is het grote verschil dat een HTML tag altijd met een kleine letter begint en een React component met een hoofdletter

Voorbeeld syntax HTML tag -> `<div />`

Voorbeeld syntax React component -> `<MyComponent />`

Met de nieuwe React 16.8 werden Hooks geïntroduceerd en deze Hooks zijn laatst ook toegevoegd aan de meest recente versie van Framer X. Hooks maakt het mogelijk om dingen te doen binnen je component zoals het aanpassen van de grote of elementen laten verdwijnen bijvoorbeeld. Hooks zorgen er voor dat Function based components hetzelfde kunnen als Class based components. Dit heeft er voor gezorgd dat de meeste mensen van Class based components zijn afgestapt. 

```
// Class based component
class KoenComponent extends React.Component {
  render() {
    return <div>Hello world!</div>
  }
}

// Function based component
function KoenComponent() {
  return <div>Hello world!</div>
}
```

**Overrides**

Wanneer je elementen ontwerpt binnen Framer X en je wilt daar code aan toevoegen voor behaviour maak je gebruik van overrides. Overrides laat je met de Framer API. Een simpel voorbeeld hiervan de is de code hier onder. Wanneer je met je muis hovert over het design element zal deze verkleinen. 

```
import { Override } from "framer"

export function Event_Hover(): Override {
    return {
        whileHover: {
            scale: 0.8,
        },
    }
}
```

## Eindopdracht
Voor de eindopdracht zou ik een nieuw ontwerp gaan maken voor de Minor Web Dev programma. Hier van was een voorbeeld te vinden op Codepen maar kon wel een update gebruiken sinds het niet heel duidelijk waar alle informatie stond en het visueel ook een betere uitstraling kon hebben. 

![huidige ontwerp](https://i.ibb.co/ZBTqQfn/Screenshot-2019-05-28-at-10-30-52.png)

Na onderzoek naar mogelijke oplossen ben ik uitgekomen op een ontwerp waar ik duidelijker wou aangeven hoe de volgorde is over de minor en heb bedacht dat het handig zou zijn om dit weer te geven in een timeline en gebruik te maken van een horizontale scroll. De kleuren heb ik ook aangepast naar 1 kleur per sprint zodat het duidelijk dat die bij elkaar horen en heb ik in plaats van de kleur te gebruiken als achtergrond kleur er voor gekozen om die te gebruiken als accent voor een cleaner gevoel van de interface. Ook de foto's van de docenten worden al getoond in het timeline elementen. 

![](https://i.ibb.co/8X5YJjS/Screenshot-2019-05-28-at-10-37-11.png)

De timeline elementen zullen uitklappen nadat de gebruiker op een element heeft geklikt. Hierna zal er meer informatie beschikbaar komen over het vak zoals hier onder word getoond in de afbeelding. 

![](https://i.ibb.co/2MfKttF/Screenshot-2019-05-28-at-11-04-03.png)

**Development**

De scroll kon ik vrij makkelijk maken met de interactieve design elementen in Framer X maar de timeline elementen ging ik van af het begin code om te oefenen met het maken van herbruikbare elementen. 

Ik begon met het toevoegen van de imports aan het begin van het document waarmee ik React importeer en de Framer API

```
import * as React from "react"
import { Stack } from "framer"
```

Ik had besloten om gebruik te maken van styled components dus deze library moest eerst worden toegevoegd aan aan mijn design document. Dit deed ik door het volgende command in te vullen in de terminal. 

```
yarn add styled-components
```

Na dat de library was toegevoegd moest ik de styled components importeren in het document met de volgende import

```
import styled from "styled-components"
```

Ik ben begonnen met het toevoegen van alle elementen binnen de container van een timeline element

```
export function Element(props) {
    return (
        <Stack
            background="white"
            borderRadius={8}
            padding={16}
            width="100%"
            height="auto"
            position="relative"
            shadow="0 1px 2px 0 rgba(0,0,0,.1)"
            whileHover={{
                y: -2,
                boxShadow: "0 5px 10px 0 rgba(0,0,0,.1)",
                cursor: "pointer",
            }}
        >
            <Wrapper>
                <ColorBar color="green" />
                <Text>
                    <Title>Hello World!</Title>
                    <Date>1 jan - 21 jan</Date>
                </Text>
                <AvatarOne backgroundImage={'url("props.imageA")'} />
                <AvatarTwo backgroundImage={'url("props.imageB")'} />
            </Wrapper>
            <Stack
                background="none"
                width="100%"
                height="auto"
                paddingTop={16}
                paddingLeft={20}
                paddingRight={16}
                alignment="start"
                direction="vertical"
            >
                <Subtitle>This is a sub title</Subtitle>
                <Description>This is a description</Description>
            </Stack>
        </Stack>
    )
}
```
Er zit wat styling in de export function zelf om de Stacks te stylen die ik binnen haal van af de Framer API. Ik moest dit doen omdat ik anders moeilijker behaviour kon toevoegen via code. De rest van de styling heb ik gedaan via styled components en zag er uit zoals hier onder. 

```
const Wrapper = styled.div`
    display: flex;
    flex-direction: row;
    width: 100%;
    height: auto;
    margin: 0;
    position: relative;
`

const ColorBar = styled.div`
    width: 4px;
    height: 37px;
    background: ${props => props.color};
    border-radius: 4px;
    margin-right: 16px;
    position: relative;
`

const Title = styled.h1`
    font-size: 16px;
    font-weight: 800;
    align-self: start;
    line-height: 1.2;
    margin: 0;
    margin-bottom: 4px;
`

const Date = styled.p`
    font-size: 12px;
    opacity: .8;
    line-height: 1.2;
    margin: 0;
`

const Text = styled.div`
    display: flex;
    flex-direction: column;
    height: auto;
`

const AvatarOne = styled.div`
    width: 36px;
    height: 36px;
    background: red;
    margin-left: auto;
    border-radius: 50%;
    background-image: ${props => props.imageA};
    background-size: cover;
    border: 4px solid #fff;
    transform: translateX(10px);
`

const AvatarTwo = styled.div`
    width: 36px;
    height: 36px;
    background-image: ${props => props.imageB};
    background: blue;
    border-radius: 50%;
    background-image: ${props => props.imageB};
    background-size: cover;
    border: 4px solid #fff;
`

const Information = styled.div`
    display: flex;
    flex-direction: column;
    align-self: flex-start;
    margin-left: 20px;
    margin-top: 32px;
    width: 100%;
`

const Subtitle = styled.h1`
    font-size: 14px;
    font-weight: 600;
    line-height: 1.2;
    margin: 0;
    margin-bottom: 4px;
`

const Description = styled.p`
    font-size: 12px;
    opacity: .8;
    line-height: 1.5;
    margin: 0;
    
`
```

De moeite in het schrijven van deze code lag hem in de syntax. Dit ziet er een stuk anders uit dan in je normaal zou doe met HTML en CSS zoals bijvoorbeeld het gebruik van camelcase en wanneer het wel en niet gebruiken van aanhalingstekens. Na veel proberen en itereren zag het element er zo uit. 

![](https://i.ibb.co/y0RwqTc/Screenshot-2019-05-28-at-11-43-56.png)

Het component was er nu maar was nog niet herbruikbaar en aan te passen binnen het canvas van Framer. Om er voor te zorgen dat er aanpassen gemaakt konden worden moest ik weer gebruik maken van de Framer API en daarna werken met props binnen het component. De eerste stap was het toevoegen van `addPropertyControls` en `ControlType` aan de import van de Framer API. 

```
import { Stack, addPropertyControls, ControlType } from "framer"
```

Na het importeren was kon ik het gaan gebruiken in development, met deze controls maak je het mogelijk om vanuit het design canvas in Framer de elementen te kunnen aanpassen zoals tekst, kleur en foto's in dit geval. Ook heb ik standard props ingevuld dat wanneer er niks word ingevuld er wel content staat. 

```
Element.defaultProps = {
    title: "Hello World!",
    date: "1 Jan - 21 Jan",
    color: "#07f",
    imageA: "https://uinames.com/api/photos/male/1.jpg",
    imageB: "https://uinames.com/api/photos/male/2.jpg",
    subtitle: "This is a subtitle",
    description: "This is a description",
}

addPropertyControls(Element, {
    title: { type: ControlType.String, title: "Title" },
    date: { type: ControlType.String, title: "Date" },
    color: { type: ControlType.Color, title: "Color bar" },
    imageA: { type: ControlType.Image, title: "Image A" },
    imageB: { type: ControlType.Image, title: "Image B" },
    subtitle: { type: ControlType.String, title: "Subtitle" },
    description: { type: ControlType.String, title: "Description" },
})
```

Dit ziet er als volgt uit het op het canvas in Framer X

![](https://i.ibb.co/1fjmL6y/Screenshot-2019-05-28-at-12-34-35.png)

Het element is nu dynamisch kan worden aangepast in het canvas zorgt er voor dat we dit element kunnen hergebruiken door heel de tijd lijn heen, het is nu een succesvol React component. De volgende stap was het toevoegen van het vergroten van het element wanneer er op geklikt werd. 

Dit behaviour van het element moest ik gaan maken aan de hand van de Framer API en begon met research naar hoe dit soort behaviour wordt gemaakt. Tijdens het onderzoek kwam ik er achter dat ik gebruik moest maken van React Hooks en `variants` van de Framer API. Om dit door te krijgen heeft even geduurd want dit vereist wat meer kennis van React en is in het begin moeilijk te begrijpen. 

Om de Hook toe te voegen heb ik deze code toegevoegd aan mijn export function

```
const [state, setState] = React.useState({
        isExpanded: false,
    })

    const expand = () => {
        setState({
            isExpanded: !state.isExpanded,
        })
    }
```

De state `isExpanded: false` heb ik daarna geven aan de container van het element en ook trigger ik het wisselen van de state via een onTap op dit element. 

```
<Stack
   onTap={expand}
   initial={state.isExpanded ? "expanded" : "default"}
   animate={state.isExpanded ? "expanded" : "default"}
   transition={{
     type: "tween",
     duration: 0.3,
   }}
>
```

De twee text layers die te voorschijn moeten komen zitten samen in een `Stack` tag en heb `variants` toegevoegd aan deze tag. Met variants kan je verschillende states van een animatie aangeven. 

```
<Stack
    variants={{
       default: { display: "none" },
       expanded: { display: "block" },
    }}
    transition={{
       type: "tween",
       duration: 0.2,
    }}
>
```

Na dit toegevoegd te hebben werkt het behaviour en klapt het element uit. Het totale React component komt er dan als volgt uit te zien. 

```
import * as React from "react"
import {
    Stack,
    addPropertyControls,
    ControlType,
    Override,
    useCycle,
} from "framer"
import styled from "styled-components"

export function Element(props) {
    const [state, setState] = React.useState({
        isExpanded: false,
    })

    const expand = () => {
        setState({
            isExpanded: !state.isExpanded,
        })
    }

    return (
        <Stack
            background="white"
            borderRadius={8}
            padding={16}
            width="100%"
            height="auto"
            position="relative"
            onTap={expand}
            shadow="0 1px 2px 0 rgba(0,0,0,.1)"
            whileHover={{
                y: -2,
                boxShadow: "0 5px 10px 0 rgba(0,0,0,.1)",
                cursor: "pointer",
            }}
            variants={{
                default: { scale: 1 },
                expanded: { scale: 1 },
            }}
            initial={state.isExpanded ? "expanded" : "default"}
            animate={state.isExpanded ? "expanded" : "default"}
            transition={{
                type: "tween",
                duration: 0.3,
            }}
        >
            <Wrapper>
                <ColorBar color={props.color} />
                <Text>
                    <Title>{props.title}</Title>
                    <Date>{props.date}</Date>
                </Text>
                <AvatarOne backgroundImage={'url("props.imageA")'} />
                <AvatarTwo backgroundImage={'url("props.imageB")'} />
            </Wrapper>
            <Stack
                background="none"
                width="100%"
                height="auto"
                paddingTop={16}
                paddingLeft={20}
                paddingRight={16}
                alignment="start"
                direction="vertical"
                variants={{
                    default: { display: "none" },
                    expanded: { display: "block" },
                }}
                transition={{
                    type: "tween",
                    duration: 0.2,
                }}
            >
                <Subtitle>{props.subtitle}</Subtitle>
                <Description>{props.description}</Description>
            </Stack>
        </Stack>
    )
}

Element.defaultProps = {
    title: "Hello World!",
    date: "1 Jan - 21 Jan",
    color: "#07f",
    imageA: "https://uinames.com/api/photos/male/1.jpg",
    imageB: "https://uinames.com/api/photos/male/2.jpg",
    subtitle: "This is a subtitle",
    description: "This is a description",
}

addPropertyControls(Element, {
    title: { type: ControlType.String, title: "Title" },
    date: { type: ControlType.String, title: "Date" },
    color: { type: ControlType.Color, title: "Color bar" },
    imageA: { type: ControlType.Image, title: "Image A" },
    imageB: { type: ControlType.Image, title: "Image B" },
    subtitle: { type: ControlType.String, title: "Subtitle" },
    description: { type: ControlType.String, title: "Description" },
})

const Wrapper = styled.div`
    display: flex;
    flex-direction: row;
    width: 100%;
    height: auto;
    margin: 0;
    position: relative;
`

const ColorBar = styled.div`
    width: 4px;
    height: 37px;
    background: ${props => props.color};
    border-radius: 4px;
    margin-right: 16px;
    position: relative;
`

const Title = styled.h1`
    font-size: 16px;
    font-weight: 800;
    align-self: start;
    line-height: 1.2;
    margin: 0;
    margin-bottom: 4px;
`

const Date = styled.p`
    font-size: 12px;
    opacity: .8;
    line-height: 1.2;
    margin: 0;
`

const Text = styled.div`
    display: flex;
    flex-direction: column;
    height: auto;
`

const AvatarOne = styled.div`
    width: 36px;
    height: 36px;
    background: red;
    margin-left: auto;
    border-radius: 50%;
    background-image: ${props => props.imageA};
    background-size: cover;
    border: 4px solid #fff;
    transform: translateX(10px);
`

const AvatarTwo = styled.div`
    width: 36px;
    height: 36px;
    background-image: ${props => props.imageB};
    background: blue;
    border-radius: 50%;
    background-image: ${props => props.imageB};
    background-size: cover;
    border: 4px solid #fff;
`

const Information = styled.div`
    display: flex;
    flex-direction: column;
    align-self: flex-start;
    margin-left: 20px;
    margin-top: 32px;
    width: 100%;
`

const Subtitle = styled.h1`
    font-size: 14px;
    font-weight: 600;
    line-height: 1.2;
    margin: 0;
    margin-bottom: 4px;
`

const Description = styled.p`
    font-size: 12px;
    opacity: .8;
    line-height: 1.5;
    margin: 0;
    
`
```

## Conclusie
Het leren van React was moeilijker dan verwacht, om te begrijpen hoe de syntax in elkaar zat heeft tijd gekost. Ook was dit de eerste keer dat ik heb gewerkt met externe libraries en API's. Dit alles bij elkaar maakte het een grote sprong van normale HTML en CSS naar het schrijven van React, Hooks en werken met API's. Het eind resultaat is ook niet precies zoals ik het voor ogen had. Het maken van de animaties heb ik nog niet helemaal door en wanneer een van de elementen veranderd overlapt deze met de onderliggende. Daarnaast is het tonen van de afbeeldingen in de elementen ook niet gelukt. Ik heb hier nog niet een goed voorbeeld van kunnen vinden. Dit zijn onderdelen waar ik nog even tijd in moet steken voor dat het werkt en het is een goed vooruitzicht dat er genoeg dingen nog te leren zijn maar tijdens de afgelopen weken heb ik wel een goede stap kunnen zetten in het leren van React en hoe React te gebruiken binnen Framer X om zo dynamische design components te maken en die interactief zijn. 



