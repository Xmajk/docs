# Intro do TypeScriptu

TypeScript je moderní programovací jazyk, který je nadmnožinou JavaScriptu. Byl vyvinut společností Microsoft a jeho hlavním cílem je přidat statické typování do JavaScriptu, což umožňuje vývojářům psát robustnější a lépe udržovatelné kódy. TypeScript se stal velmi populárním, zejména v prostředí velkých projektů a aplikací, kde je důležitá struktura a typová bezpečnost.

Klíčové vlastnosti TypeScriptu
---
    1) Statické typování: TypeScript umožňuje definovat typy proměnných, funkcí a objektů. To pomáhá odhalit chyby již při kompilaci, což zvyšuje kvalitu kódu.
    2) Podpora moderních funkcí JavaScriptu: TypeScript podporuje všechny funkce JavaScriptu, včetně těch nejnovějších, jako jsou asynchronní funkce, moduly a další.
    3) Rozšiřitelnost: TypeScript umožňuje rozšiřovat existující JavaScriptové knihovny a frameworky. Můžete snadno integrovat TypeScript do stávajících projektů.
    4) IntelliSense: Díky statickému typování nabízí TypeScript v IDE (např. Visual Studio Code) pokročilé funkce jako automatické doplňování kódu, nápovědu a refaktoring.

## Odkazy

- [oficiální dokumentace](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html)
- [w3schools](https://www.w3schools.com/typescript/index.php)

## Typescript a React

:::info

V době tvorby poznámek aktuální verze **Reactu 19** nefunguje u ní typescript, proto je potřeba používat **React 18**

    ```bash
    npm uninstall react react-dom
    npm install react@18 react-dom@18
    ```

    :::warning

    Nejde ani změnění verze reactu, ale funguje packet manager `yarn`

        ```bash title="instalace yarnu"
        npm install --global yarn
        ```

        ```bash
        yarn create react-app my-app --template typescript
        ```
:::

```bash title="vytvoření typescript reactu"
npx create-react-app my-app --template typescript
```

<div
    style={{
        background:"transparent",
        width:"100%",
        height:"150px"
    }}
>
    <img
    alt=""
    src="/img-docs/typescript/Typescript_logo_2020.svg.png"
    style={{height:"100%"}}
    ></img>
</div>
