# Contribution Guidelines

## Always think about the user

The number one pillar for contribution is to **ALWAYS** think about how the user will use the library. 

Put yourself in their position, and imagine how they would feel about your feature you wrote.

1. Is it easy to use? 
2. Has it been documented well?
3. Is it intuative?
4. Is it consistent with the rest of the API?
5. Is it fun to use?

## Good Commit Names

Please write good commit messages when making a commit: https://chris.beams.io/posts/git-commit/

**Do not:**
```
c // What?
rtl // Adding acryonyms without explaining anything else is not helpful
works! // Glad its working, but the message is not helpful
demo updated // Getting better, but capitalize the first letter
Unesesary coment removed // Make sure to use correct spelling
```

## Writing Code

*   Include documentation reference(s) at the top of each file:

    ```js
    // http://officeopenxml.com/WPdocument.php
    ```

*   Follow Prettier standards, and consider using the [Prettier VSCode](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) plugin.

*   Follow the `TSLint` rules

## Add vs Create

This is just a guideline, and the rules can sometimes be broken.

*   Use `create` if the method `new`'s up an element inside:

    ```js
    public createParagraph() {
        const paragraph = new Paragraph();
        this.root.push(paragraph);
    }
    ```

*   Use `add` if you add the element into the method as a parameter:

    ```js
    public addParagraph(paragraph: Paragraph) {
        this.root.push(paragraph);
    }
    ```

## Getters and Setters

Getters and Setters are done with a capital letter like so:

```js
public get Level() {

}
```

There is no performance advantage by doing this. It means we don't need to prefix all private variables with the ugly `_`:

**Do not:**

```js
private get _level: string;
```

**Do**

```js
private get level: string;
```

## Interfaces over type alias

Do not use `type`, but rather use `Interfaces`. `type` cannot be extended, and a class cannot implement it.

> "In general, use what you want ( type alias / interface ) just be consistent"
> "always use interface for public API's definition when authoring a library or 3rd party ambient type definitions"
>
> *   https://medium.com/@martin_hotell/interface-vs-type-alias-in-typescript-2-7-2a8f1777af4c

`Interface` is generally preferred over `type`: https://stackoverflow.com/questions/37233735/typescript-interfaces-vs-types

**Do not:**

```js
type RelationshipFileInfo = { id: number, target: string };
```

**Do:**

```js
interface IRelationshipFileInfo {
    id: number;
    target: string;
}
```

## String enums vs type

To take full advantage of TypeScript's typing system, its best to use `string enums`:

**Do not:**

```js
type WeaponType = "bow" | "sword" | "wand";
```

**Do:**

```js
enum WeaponType = {
    BOW = "bow",
    SWORD = "sword",
    WAND = "wand",
}
```

## Spell correctly, full and in American English

I am not sure where these habit in software development comes from, but I do not believe it is beneficial:

**Do not:**
```js
readdy // misspelling
perm // abbreviation
conf // abbreviation
cnty // abbreviation
relationFile // abbreviation
colour // U.K. English
```

**Do:**
```js
ready
permission
config
country
relationshipFile
color
```

## Keep files small (within reason)

To minimize merge conflicts, reduce complexity, and improve readability, keep the files small.

## Name files and folders with `/foo-bar/kebab-case.ts`

To be consistent and in-line with the project, name files `like-this.ts`.

https://stackoverflow.com/questions/7273316/what-is-the-javascript-filename-naming-convention

## Testing

Please write a test of every file you make and suffix it with `.spec.ts`.

Here is a template of a test:

```js
import { assert } from "chai";

describe("ClassName", () => {
    beforeEach(() => {
        // TODO
    });

    describe("#methodName()", () => {
        it("should ", () => {
            // TODO
        });
    });
});
```

Try not to use the `tests/utility.ts` file as this is being deprecated.
