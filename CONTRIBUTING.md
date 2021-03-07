#  Contributing Guidelines  #

If you were linked to this file, it is probably because you want to contribute to a repository owned by [kibigo!](https://github.com/marrus-sh).
Instead of congratulating you for that, this file is here to give you some advice.


##  Before You Even Think About It  ##

You should take a nice humility pill and take a moment to analyse your motives for being here.
Since you are looking to contribute to an opensource project, it is *probably* either because :— (1) you have an economic incentive to do so, or (2) because you hold some utopian image of people being stronger or better when they all collaborate in a shared commons.
If you fall into the latter camp, **there is a good chance you are white, and male,** *not* because white men are the only people in opensource, but because white men are the people who most strongly and fervently cling to the idea of a “shared public commons” in the face of ever‐increasing evidence that :— (a) the culture and (b) its products —: of the opensource movement are neither “shared” nor “common” (we can leave the question of “public” to another day).

**You should stop to consider the fact that not everybody has the same assumptions, expectations, or goals,** and this extends from little things like code style to medium things like documentation language to big things like project aims and architectural concerns.
There is a *good* chance, if you have not stopped to consider this, that through contributing, part of what you are hoping to achieve is to simply make the source code reflect yourself more; which is to say that your contribution is not about utopian public commons at all, but rather **simply about making everything all about you.**

The fact of the matter is that **software is made by humans, who belong to a culture,** and this goes for you and me and everybody else interacting with this site.
Software is both **culturally‐situated** and **a cultural product**, and like anything which can be described with those words, it comes with certain ethical responsibilities regarding dissemination, participation, appropriate use, *et cetera*, absolutely **none** of which can be handled through legal frameworks such as an opensource license.

**I hate to break it to you, opensource software developer, but the files in these repositories are texts written by (and for) human beings, and if you don’t have a critical framework on hand for dealing with texts written by (and for) human beings, I suggest you get one** because you have been *severely* misled about the work you have been doing all this time.

**I encourage you to think of the programs here·in less as code and more as recipes or rituals.**
When you go around adding butter to everything because you think “it just tastes better”, I promise you, we can all tell.


##  After You Have Thought About It  ##

I am not particularly interested in one·off patches from members outside the community, for reasons which should be evident from the above.
I encourage you to reach out to me directly if you want to participate in a meaningful, lasting way.
I try to keep my contact information up·to·date [on my GitHub public profile](https://github.com/marrus-sh/marrus-sh); for the forseeable future this will likely be [via the Mastodon‐compatible fediverse](https://joinmastodon.org).

If your contribution is not material (i.e., not representable in bytes on a hard disk, but something more intangible, like an idea or criticism), for repositories with GitHub Discussions enabled, that may be a more suitable option.
If you have an Issue with something, feel free to file an Issue.
Be advised that if I have not seen you around, and your connection to the project or its community is not evident, I may not particularly care what you think.

You should be familiar with the [Standards of Participation](./CODE_OF_CONDUCT.md) before participating.


##  KIBI House Style  ##

The following documents the *basics* of the house style which I use for the bulk of my projects.
It should be enough to get you started writing and understanding the code.
You should *expect* to receive comments regarding “the preferred way of writing X” with any code you submit via a PR, and take these comments to heart for your next contribution.

**Regardless of language, all code should use tabs for indentation** unless the language itself makes this prohibitive.
One exception is in Markdown (including Markdown comments in other languages), in which four spaces is conventional.


###  Swift code  ###


####  File structure  ####

Within each module, the file structure is as follows:

| Path | Meaning |
| --- | --- |
| `Classes/` | Class type definitions |
| `Functions/` | Toplevel function definitions |
| `Protocols/` | Protocol definitions |
| `Values/` | Value type definitions (structs and enums) |
| `Operators.swift` | Any operators defined in this module, as well as any toplevel operator definitions |
| `Precedences.swift` | Operator precedences if required |

Toplevel constant or variable declarations are to be *avoided at all costs* (make them a static property on a type).

Extensions to types go in the same file as the type’s declaration, or in the place where the type’s declaration *would* go (for types declared in other modules).
Files are named based on the thing they define; append the module name for things declared in other modules.
For example, an extension to `String` should go in `Values/Swift.String.swift`.

Typealiases get their own file, organized by the aliased type.
Place extensions to an aliased type in the same file as the typealias.


####  Character input  ####

The allowed characters in Swift code are those in the [MacRoman character set](https://en.wikipedia.org/wiki/Mac_OS_Roman) plus any Emoji; these are all characters which should be available through ordinary Macintosh input methods.
(Linux users: You should be able to install a Macintosh keyboard layout on your system; I cannot help you when it comes to emoji [but recommend [fcitx](https://fcitx-im.org/wiki/Fcitx)].)

Exceptions to the above are allowed for:

 +  String literals
 +  Documentation comments
 +  Identifiers, when an accepted form uses other characters (for example, identifiers in a different language)


####  Naming conventions  ####

The usual Swift naming conventions apply.
However, the names given in specifications take priority; this is especially true of grammars.
In some cases the specification name is a little more opaque or cumbersome than the common name which you might expect; oftentimes, maintaining this is important, because another specification will later redefine the common name with slightly different semantics.

The character `U+00B7 · MIDDLE DOT` is used in place of a hyphen; the following letter is not capitalized.
It is also used in abbreviations in place of Swift’s more idiomatic “write all the letters with the same case” convention; in this case, the following letter *is* capitalized.

Properties, functions, or methods explicitly provided for by a specification are written surrounded by middle dots, like `·this·`; this is to distinguish them from both (a) grammars et cetera which might have the same name, and (b) the idiomatic Swift interfaces, where better ones exist.
In the actual specifications, you might see `[this]` or `·this·` or `{this}` or similar.


#####  emoji  #####

Emoji may be used in non‐public identifiers *only*.
The emoji `🙈`, `🙉`, `🙊` are used to denote changes in access control, signifying `private`, `fileprivate`, and `internal`, respectively.
It is *recommended* that constants and variables declared in the body of a function (or other statement) use an emoji in their name, to distinguish them from arguments and parameters.

The following are broad emoji conventions for use in such local contexts:

| Emoji | Meaning |
| :-: | :-: |
| `🔙` | The result of a function call |
| `🔜` | What will be returned |
| `🤛` | Righthand‐side |
| `🤜` | Lefthand‐side |
| `🆕` | A newly‐created value |
| `🆗` | OK; success |
| `🆖` | No good; failure |
| `〽️` | Mutable; variable |

Emoji may be used as operators even in public code (where the Swift lexical grammar allows).

**Be aware that some emoji include an invisible VS-16 codepoint (`U+FEOF`).**


####  Documentation conventions  ###

Documentation should follow [ordinary Swift conventions](https://developer.apple.com/library/archive/documentation/Xcode/Reference/xcode_markup_formatting_ref/SymbolDocumentation.html).
All public API terms should be documented, and each should have a `Version` callout describing when they were added.

An `Authors` callout should be used for functions and computed properties (anything which might appear within an extension), but *not* for types or protocol requirements.
All contributors to the implementation should put their names here.

Use `Note` callouts for documenting ambiguous cases in the spec, differences in the implementation, or common gotchas with use.

Functions which take parameters should have a `Parameters` section; functions which return should have a `Returns`, and functions which throw should have a `Throws`.


###  Other code languages  ###

There are no explicit conventions; try to match existing code.