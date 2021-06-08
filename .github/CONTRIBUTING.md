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


##  Branches and Versions  ##

The main branch of most repositories will be called `current`; this is the code which is recommended for new users to adopt.
It is not guaranteed to be stable, only the most stable; it is not guaranteed to be complete, only the most complete.
In addition to this branch, there will (likely) be tagged releases; `current` may contain additional commits beyond the latest tagged release, but typically only in the case of documentation or metadata updates (not changes to code).

Releases take the usual three‐part decimal format used by [SemVer](https://semver.org) and other open source projects.
The terms *version*, *draft*, and *revision* are sometimes preferred over *major*, *minor*, and *patch*, and you will sometimes see them formatted as `vXdYrZ` or `X.Y / revision Z` instead of the `X.Y.Z` which is conventional.

Development for the next draft (major or minor) release typically occurs on the `development` branch.
Pull requests which make code changes should be sent there if one exists.


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

Filenames may optionally be preceded by an emoji sigil, followed by a space.
**_Use emoji sigils to associate code with relevant documentation_**; for example if a documentation section is titled `🏳️‍🌈 Gay Shit`, one might name a file documented in that section `🏳️‍🌈 Trains.swift` (not `🚂 Trains.swift`) to associate it with the other files so documented.
This makes it easier to operate on related sections of the code using filename globs and also makes it much easier to find the file you’re looking for in large(r) codebases.


####  Character input  ####

The allowed characters in Swift code are those in the [MacRoman character set](https://en.wikipedia.org/wiki/Mac_OS_Roman) plus any Emoji; these are all characters which should be available through ordinary Macintosh input methods.
(Linux users: You should be able to install a Macintosh keyboard layout on your system; I cannot help you when it comes to emoji [but recommend [fcitx](https://fcitx-im.org/wiki/Fcitx)].)

Exceptions to the above are allowed for:

 +  String literals
 +  Documentation comments (although *do your best*)
 +  Identifiers, when an accepted form uses other characters (for example, identifiers in a different language)


####  Naming conventions  ####

The usual Swift naming conventions apply.
However, the names given in specifications take priority; this is especially true of grammars.
In some cases the specification name is a little more opaque or cumbersome than the common name which you might expect; oftentimes, maintaining this is important, because another specification will later redefine the common name with slightly different semantics.

The character `U+00B7 · MIDDLE DOT` is used in place of a hyphen; the following letter is not capitalized.
It is also used in abbreviations in place of Swift’s more idiomatic “write all the letters with the same case” convention; in this case, the following letter *is* capitalized.


#####  middot names  #####

When a property, function, or method implements an algorithm explicitly provided for by a specification, describes a value, or otherwise forms a core part of the set of expected interactions within an API, its name will be written surrounded by middle dots, like `·this·`.
Most properties, functions, and methods should take this form.
A middle dot is **not** used in the following cases:

 +  Names of types or specific values (e.g. enum cases)
 +  Simple conversions between types (e.g. `.string` or `.int` computed properties)
 +  Properties or methods required for protocol conformance (although these may be implemented simply as aliases for a middot property or method)
 +  Implementation of native Swift APIs like `CustomStringConvertible` (for obvious reasons)

Outside of protocol implementations, you should *always* use middot methods where available; they are the preferred means of interacting with code.


#####  emoji  #####

Emoji may be used in non‐public identifiers *only*.
The emoji `🙈`, `🙉`, `🙊` are used to denote changes in access control, signifying private, fileprivate, and internal, respectively.
If an internal property or method is `@usableFromInline`, this may be indicated with a `🐵` emoji instead.
It is *recommended* that constants and variables declared in the body of a function use an emoji in their name, to distinguish them from properties and parameters.

The following are broad emoji conventions for use in such local contexts:

| Codepoint(s) | Emoji | Meaning |
| --: | :-: | :-: |
| `U+2319,U+FE0F` | `ℹ️` | Index |
| `U+303D,U+FE0F` | `〽️` | Mutable; variable |
| `U+1F192` | `🆒` | Processed |
| `U+1F195` | `🆕` | A newly‐created value |
| `U+1F196` | `🆖` | No good; failure |
| `U+1F197` | `🆗` | OK; success |
| `U+1F198` | `🆘` | Unsafe |
| `U+1F199` | `🆙` | Currently up; a value to process |
| `U+1F201` | `🈁` | “Here”; the current value in an iteration/loop |
| `U+1F435` | `🐵` | `@usableFromInline internal` |
| `U+1F4B1` | `💱` | A typecast or conversion |
| `U+1F519` | `🔙` | The return value of an operation |
| `U+1F51A` | `🔚` | A last value |
| `U+1F51C` | `🔜` | A collection being reduced into; a forthcoming result |
| `U+1F51A` | `🔝` | A first value |
| `U+1F648` | `🙈` | `private` |
| `U+1F649` | `🙉` | `fileprivate` |
| `U+1F64A` | `🙊` | `internal` |
| `U+1F91B` | `🤜` | Lefthand‐side |
| `U+1F91C` | `🤛` | Righthand‐side |

Emoji may be used as operators even in public code (where the Swift lexical grammar allows).

**Be aware that some emoji include an invisible VS-16 codepoint (`U+FE0F`).**


####  Documentation conventions  ###

Documentation should follow [ordinary Swift conventions](https://developer.apple.com/library/archive/documentation/Xcode/Reference/xcode_markup_formatting_ref/SymbolDocumentation.html).
All public API terms should be documented, and each should have a `Version` callout describing when they were added.

An `Authors` callout should be used for functions and computed properties (anything which might appear within an extension), but *not* for types or protocol requirements.
All contributors to the implementation should put their names here.

Use `Note` callouts for documenting ambiguous cases in the spec, differences in the implementation, or common gotchas with use.

Functions which take parameters should have a `Parameters` section; functions which return should have a `Returns`, and functions which throw should have a `Throws`.


###  Other code languages  ###

There are no explicit conventions; try to match existing code.
