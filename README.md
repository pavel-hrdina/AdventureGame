# Adventure Game

A learning project to create a text-based adventure game.
I hope you enjoy playing the game, I had fun creating it.

[![Code of Conduct](https://img.shields.io/badge/Contributor%20Covenant-2.0-4baaaa.svg)](./docs/CODE_OF_CONDUCT)
[![Contributing](https://img.shields.io/badge/Contributing-Guide-4baaaa.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

image of the game intro screen will be here as png

# Table of contents

- [Adventure Game](#adventure-game)
- [Description](#description)
- [How to play](#how-to-play)
- [How to run](#how-to-run)
- [How to build](#how-to-build)
- [Documentation](#documentation)
- [License](#license)
- [Contributing](#contributing)
- [Code of Conduct](#code-of-conduct)
- [Acknowledgments](#acknowledgments)
- [Authors](#authors)

## Description

This is a text-based adventure game implemented in Java.
When ever I am learning a new programming 
language, I like to implement a text-based adventure game.


It is a fun way to learn the basics of the language. 
I like to use object-oriented programming to implement the game.
But I also like to keep it simple and not over-engineer it.

## How to play

The game is a text-based adventure game. You play as a human 
explorer. You are exploring a dungeon with the goal of
finding the treasure and then escaping the dungeon. In the 
dungeon you will encounter monsters and traps that you must 
overcome.

You will also find items that will help you in your
quest. You will need to make choices on which way to go and
what to do. I hope you enjoy playing the game. There are no
graphics, just text. Use your imagination, there is no 
hand-holding in this game. You will need to figure out what
to do on your own.

## How to run

To run the game, install one of the pre-built binaries from the
[releases](https://github.com/pavel-hrdina/AdventureGame/releases) page. 
Then run the binary from the command line. The bineries are generated 
automatically by the CI/CD pipeline that I have set up for this project. 
the binaries are built for Windows, MacOS, and Linux while supporting x86, 
x64 , arm, and arm64 architectures. 

## How to build

To build the game from source, you will need to have Java installed
on your system using the [GraalVM](https://www.graalvm.org/downloads/) JDK
. You will also need to have gradle installed. I use
IntelliJ IDEA as my IDE, but you can use any IDE that you like.

To build the game:

1. Clone the repository

```shell
git clone repo
```

2. Open the project in your IDE or use the command line

3. Build the project native image using the gradle task `nativeCompile`

```shell
gradle nativeCompile
```

4. Run the game

```shell
./build/native/nativeCompile/AdventureGame
```

## Documentation

The game is documented using JavaDoc. The code is also commented. You can
find the JavaDoc in the `docs` folder. I will also be including diagrams. 
Brainstorming, flowcharts, and pseudocode that I made while creating the game, 
to serve as documentation.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on 
our code of conduct, and the process for submitting pull requests to me.

## Code of Conduct

Please read [CODE_OF_CONDUCT.md](./docs/CODE_OF_CONDUCT) for details on our code of conduct.

## Acknowledgments

- [Text Adventure Game](https://en.wikipedia.org/wiki/Text-based_game)

A great read on text-based adventure games, the history and how they work.

- [The Startup Guide to Storytelling: Learn from Text-Based Adventure Games!](https://www.taskade.com/blog/text-based-storytelling-games-startup-business/)

An interesting article on how text-based adventure games can be used to tell stories. 
I used some of the ideas in this article to create the story for the game.

- [Text-Adventure-Tutorial - GitHub](https://github.com/Kyle-L/Text-Adventure-Tutorial)

A great tutorial on how to create a text-based adventure game in Python.
It also explains some general programming concepts like flowcharts and pseudocode,
modelíng and design, and testing. I used the ideas in this tutorial to create the game.

## Authors

- Pavel Hrdina - [pavel-hrdina](https://github.com/pavel-hrdina)