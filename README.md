<<<<<<< HEAD
<p align="center">
  <a href="" rel="noopener">
 <img width=200px height=200px src="https://i.imgur.com/FxL5qM0.jpg" alt="Bot logo"></a>
</p>

<h3 align="center">Bot Name</h3>

<div align="center">

  [![Status](https://img.shields.io/badge/status-active-success.svg)]()
  [![Platform](https://img.shields.io/badge/platform-reddit-orange.svg)](https://www.reddit.com/user/Wordbook_Bot)
  [![GitHub Issues](https://img.shields.io/github/issues/kylelobo/The-Documentation-Compendium.svg)](https://github.com/kylelobo/The-Documentation-Compendium/issues)
  [![GitHub Pull Requests](https://img.shields.io/github/issues-pr/kylelobo/The-Documentation-Compendium.svg)](https://github.com/kylelobo/The-Documentation-Compendium/pulls)
  [![License](https://img.shields.io/badge/license-MIT-blue.svg)](/LICENSE)

</div>

---

<p align="center"> 🤖 Few lines describing what your bot does.
    <br>
</p>

## 📝 Table of Contents
+ [About](#about)
+ [Demo / Working](#demo)
+ [How it works](#working)
+ [Usage](#usage)
+ [Getting Started](#getting_started)
+ [Deploying your own bot](#deployment)
+ [Built Using](#built_using)
+ [TODO](../TODO.md)
+ [Contributing](../CONTRIBUTING.md)
+ [Contributing](../CONTRIBUTORS.md)
+ [Authors](#authors)
+ [Acknowledgments](#acknowledgement)

## 🧐 About <a name = "about"></a>
Write about 1-2 paragraphs describing the purpose of your bot.

## 🎥 Demo / Working <a name = "demo"></a>
![Working](https://media.giphy.com/media/20NLMBm0BkUOwNljwv/giphy.gif)

## 💭 How it works <a name = "working"></a>

The bot first extracts the word from the comment and then fetches word definitions, part of speech, example and source from the Oxford Dictionary API.

If the word does not exist in the Oxford Dictionary, the Oxford API then returns a 404 response upon which the bot then tries to fetch results form the Urban Dictionary API.

The bot uses the Pushshift API to fetch comments, PRAW module to reply to comments and Heroku as a server.

The entire bot is written in Python 3.6

## 🎈 Usage <a name = "usage"></a>

To use the bot, type:
```
!dict word
```
The first part, i.e. "!dict" **is not** case sensitive.

The bot will then give you the Oxford Dictionary (or Urban Dictionary; if the word does not exist in the Oxford Dictionary) definition of the word as a comment reply.

### Example:

> !dict what is love

**Definition:**

Baby, dont hurt me~
Dont hurt me~ no more.

**Example:**

Dude1: Bruh, what is love?
Dude2: Baby, dont hurt me, dont hurt me- no more!
Dude1: dafuq?

**Source:** https://www.urbandictionary.com/define.php?term=what%20is%20love

---

<sup>Beep boop. I am a bot. If there are any issues, contact my [Master](https://www.reddit.com/message/compose/?to=PositivePlayer1&subject=/u/Wordbook_Bot)</sup>

<sup>Want to make a similar reddit bot? Check out: [GitHub](https://github.com/kylelobo/Reddit-Bot)</sup>

## 🏁 Getting Started <a name = "getting_started"></a>
These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See [deployment](#deployment) for notes on how to deploy the project on a live system.

### Prerequisites

What things you need to install the software and how to install them.

```
Give examples
```

### Installing

A step by step series of examples that tell you how to get a development env running.

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo.

## 🚀 Deploying your own bot <a name = "deployment"></a>
To see an example project on how to deploy your bot, please see my own configuration:

+ **Heroku**: https://github.com/kylelobo/Reddit-Bot#deploying_the_bot

## ⛏️ Built Using <a name = "built_using"></a>
+ [PRAW](https://praw.readthedocs.io/en/latest/) - Python Reddit API Wrapper
+ [Heroku](https://www.heroku.com/) - SaaS hosting platform

## ✍️ Authors <a name = "authors"></a>
+ [@kylelobo](https://github.com/kylelobo) - Idea & Initial work

See also the list of [contributors](https://github.com/kylelobo/The-Documentation-Compendium/contributors) who participated in this project.

## 🎉 Acknowledgements <a name = "acknowledgement"></a>
+ Hat tip to anyone whose code was used
+ Inspiration
+ References



<p align="center">
  <a href="" rel="noopener">
 <img src="https://i.imgur.com/AZ2iWek.png" alt="Project logo"></a>
</p>
<h3 align="center">Project Title</h3>

<div align="center">

  [![Hackathon](https://img.shields.io/badge/hackathon-name-orange.svg)](http://hackathon.url.com)
  [![Status](https://img.shields.io/badge/status-active-success.svg)]()
  [![GitHub Issues](https://img.shields.io/github/issues/kylelobo/The-Documentation-Compendium.svg)](https://github.com/kylelobo/The-Documentation-Compendium/issues)
  [![GitHub Pull Requests](https://img.shields.io/github/issues-pr/kylelobo/The-Documentation-Compendium.svg)](https://github.com/kylelobo/The-Documentation-Compendium/pulls)
  [![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE.md)

</div>

---

<p align="center"> Few lines describing your project.
    <br>
</p>

## 📝 Table of Contents
- [Problem Statement](#problem_statement)
- [Idea / Solution](#idea)
- [Dependencies / Limitations](#limitations)
- [Future Scope](#future_scope)
- [Setting up a local environment](#getting_started)
- [Usage](#usage)
- [Technology Stack](#tech_stack)
- [Contributing](../CONTRIBUTING.md)
- [Authors](#authors)
- [Acknowledgments](#acknowledgments)

## 🧐 Problem Statement <a name = "problem_statement"></a>
It is useful to design and follow a specific format when writing a problem statement. While there are several options
for doing this, the following is a simple and straightforward template often used in Business Analysis to maintain
focus on defining the problem.

- IDEAL: This section is used to describe the desired or “to be” state of the process or product. At large, this section
should illustrate what the expected environment would look like once the solution is implemented.
- REALITY: This section is used to describe the current or “as is” state of the process or product.
- CONSEQUENCES: This section is used to describe the impacts on the business if the problem is not fixed or improved upon.
This includes costs associated with loss of money, time, productivity, competitive advantage, and so forth.

Following this format will result in a workable document that can be used to understand the problem and elicit
requirements that will lead to a winning solution.

## 💡 Idea / Solution <a name = "idea"></a>
This section is used to describe potential solutions.

Once the ideal, reality, and consequences sections have been
completed, and understood, it becomes easier to provide a solution for solving the problem.

## ⛓️ Dependencies / Limitations <a name = "limitations"></a>
- What are the dependencies of your project?
- Describe each limitation in detailed but concise terms
- Explain why each limitation exists
- Provide the reasons why each limitation could not be overcome using the method(s) chosen to acquire.
- Assess the impact of each limitation in relation to the overall findings and conclusions of your project, and if
appropriate, describe how these limitations could point to the need for further research.

## 🚀 Future Scope <a name = "future_scope"></a>
Write about what you could not develop during the course of the Hackathon; and about what your project can achieve
in the future.

## 🏁 Getting Started <a name = "getting_started"></a>
These instructions will get you a copy of the project up and running on your local machine for development
and testing purposes. See [deployment](#deployment) for notes on how to deploy the project on a live system.

### Prerequisites

What things you need to install the software and how to install them.

```
Give examples
```

### Installing

A step by step series of examples that tell you how to get a development env running.

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

## 🎈 Usage <a name="usage"></a>
Add notes about how to use the system.

## ⛏️ Built With <a name = "tech_stack"></a>
- [MongoDB](https://www.mongodb.com/) - Database
- [Express](https://expressjs.com/) - Server Framework
- [VueJs](https://vuejs.org/) - Web Framework
- [NodeJs](https://nodejs.org/en/) - Server Environment

## ✍️ Authors <a name = "authors"></a>
- [@kylelobo](https://github.com/kylelobo) - Idea & Initial work

See also the list of [contributors](https://github.com/kylelobo/The-Documentation-Compendium/contributors)
who participated in this project.

## 🎉 Acknowledgments <a name = "acknowledgments"></a>
- Hat tip to anyone whose code was used
- Inspiration
- References





























# ProjectTemplate v0.2 ![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/v/release/flagarde/ProjectTemplate?include_prereleases) ![GitHub](https://img.shields.io/github/license/flagarde/ProjectTemplate) ![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/flagarde/ProjectTemplate) ![GitHub repo size](https://img.shields.io/github/repo-size/flagarde/ProjectTemplate) ![GitHub language count](https://img.shields.io/github/languages/count/flagarde/ProjectTemplate) ![GitHub forks](https://img.shields.io/github/forks/flagarde/ProjectTemplate?style=plastic) ![GitHub stars](https://img.shields.io/github/stars/flagarde/ProjectTemplate?style=plastic) ![GitHub watchers](https://img.shields.io/github/watchers/flagarde/ProjectTemplate) ![GitHub last commit](https://img.shields.io/github/last-commit/flagarde/ProjectTemplate?style=plastic) ![GitHub (Pre-)Release Date](https://img.shields.io/github/release-date-pre/flagarde/ProjectTemplate) ![GitHub contributors](https://img.shields.io/github/contributors-anon/flagarde/ProjectTemplate) #
=======
# ProjectTemplate v0.2 ![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/v/release/flagarde/ProjectTemplate?include_prereleases) ![GitHub](https://img.shields.io/github/license/flagarde/ProjectTemplate) ![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/flagarde/ProjectTemplate) ![GitHub repo size](https://img.shields.io/github/repo-size/flagarde/ProjectTemplate) ![GitHub language count](https://img.shields.io/github/languages/count/flagarde/ProjectTemplate) ![GitHub forks](https://img.shields.io/github/forks/flagarde/ProjectTemplate) ![GitHub stars](https://img.shields.io/github/stars/flagarde/ProjectTemplate) ![GitHub watchers](https://img.shields.io/github/watchers/flagarde/ProjectTemplate) ![GitHub last commit](https://img.shields.io/github/last-commit/flagarde/ProjectTemplate) ![GitHub (Pre-)Release Date](https://img.shields.io/github/release-date-pre/flagarde/ProjectTemplate) ![GitHub contributors](https://img.shields.io/github/contributors-anon/flagarde/ProjectTemplate) #
>>>>>>> a65a41d9082077df61827baf3936846c8a7c3598

## Template for C++ projects ##
[📘 Documentation](https://flagarde.github.io/ProjectTemplate/)

## Builds ##
|                   | Linux clang       | Linux gcc         | macOS clang       | Windows MSVC      | Windows MinGW     |
|:-----------------:|:-----------------:|:-----------------:|:-----------------:|:-----------------:|:-----------------:|
|Github             |![1]               |![2]               |![3]               |![4]               |![5]               |
|Travis             |[![6]][0]          |[![7]][0]          |[![8]][0]          |[![9]][0]          |       ❌          |

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/e6a6bfa2dbef4060a99fdfe1ef244a9e)](https://app.codacy.com/manual/flagarde/ProjectTemplate?utm_source=github.com&utm_medium=referral&utm_content=flagarde/ProjectTemplate&utm_campaign=Badge_Grade_Dashboard)
[![CodeFactor](https://www.codefactor.io/repository/github/flagarde/ProjectTemplate/badge)](https://www.codefactor.io/repository/github/flagarde/ProjectTemplate)

[![codecov](https://codecov.io/gh/flagarde/ProjectTemplate/branch/master/graph/badge.svg)](https://codecov.io/gh/flagarde/ProjectTemplate)

[1]: https://img.shields.io/github/workflow/status/flagarde/ProjectTemplate/Linux%20Clang
[2]: https://img.shields.io/github/workflow/status/flagarde/ProjectTemplate/Linux%20GCC
[3]: https://img.shields.io/github/workflow/status/flagarde/ProjectTemplate/macOS
[4]: https://img.shields.io/github/workflow/status/flagarde/ProjectTemplate/Windows%20MSVC
[5]: https://img.shields.io/github/workflow/status/flagarde/ProjectTemplate/Windows%20MinGW

[6]: https://travis-matrix-badges.herokuapp.com/repos/flagarde/ProjectTemplate/branches/master/1?use_travis_com=true
[7]: https://travis-matrix-badges.herokuapp.com/repos/flagarde/ProjectTemplate/branches/master/2?use_travis_com=true
[8]: https://travis-matrix-badges.herokuapp.com/repos/flagarde/ProjectTemplate/branches/master/3?use_travis_com=true
[9]: https://travis-matrix-badges.herokuapp.com/repos/flagarde/ProjectTemplate/branches/master/4?use_travis_com=true
[10]:❌
[0]: https://travis-ci.org/flagarde/ProjectTemplate
