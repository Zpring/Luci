<table align="center"><tr><td align="center" width="9999">

<img src="https://images.generated.photos/jqguEfsi0Q7fghDlnuQ-KPkFkalSLGNHcgTIBMLVMyw/rs:fit:512:512/Z3M6Ly9nZW5lcmF0/ZWQtcGhvdG9zL3Yz/XzA5MTU5MzkuanBn.jpg" align="center" width="170" alt="Project icon">

# LUCI

*Logical Unity for Communicational Interactivity*

</td></tr>

</table>    

<div align="center">

> [![Version badge](https://img.shields.io/badge/version-0.1.0-silver.svg)](https://lisa--brunolcarli.repl.co/graphql/?query=query%7B%0A%09lisa%0A%7D)
[![Docs Link](https://badgen.net/badge/docs/github_wiki?icon=github)](https://github.com/brunolcarli/Luci/wiki)
[![test badge](https://img.shields.io/badge/test-failing-red.svg)](https://lisa--brunolcarli.repl.co/graphql/?query=query%7B%0A%09lisa%0A%7D)

LUCI is a conversational tamabotchi for discord.

</div>


## Developers

### Cloning and executing

![Linux Badge](https://img.shields.io/badge/OS-Linux-black.svg)
![Apple badge](https://badgen.net/badge/OS/OSX/:color?icon=apple)


#### Local machine


Clone this project and engage a **python3** virtual environment the way as you like and install the requirements through Makefile.

Example using virtualevwrapper:

```
$ git clone https://github.com/brunolcarli/Luci.git
$ cd luci/
$ mkvirtualenv Luci
$ (Luci) make install
```


Create a `.env` file and add the following content:

```
TOKEN=<your_test_bot_token>
LISA_URL=<lisa_url>
BOT_API=<quotes_api_url>
BACKEND_URL=None
SETTINGS_MODULE=development
```

You should configure your own environment cloning both lisa and bot api:

- `LISA_URl` is required since the bot requests text offense and sentiment to the service API.

- `BOT_API` is only required for quoting commands. This may be removed on future versions, since it is planed to be merged on the ~~undeveloped yet~ `BACKEND_URL`

Note: If `SETTINGS_MODULE=production` the bot will run on a flask server instance.

Execute the bot:

```
$ (Luci) make run
```

### Training Models

The bot is trained over a serie of .`json` datasets on `core/training/json/intentions/`.

For each intention directory there are located a serie of `dataset_x.json` qhere `x` is a sequence number of the train dataset. You can create a new one containing the text and training target label on the following shape:

```json
[
    {"text": "An example text.", "intention": 1},
    {"text": "Another example text.", "intention": 1},
    {"text": "Way othe example text.", "intention": 2},
    {"text": "keep going.", "intention": 2}
]
```

The training data **must** respect the intention archicture proposed on the docs, otherwise it may cause the model to behave unproperly.

Train data through Makefile:

```
$ (Luci) make train
```

You can view some models score and the number o sample data used for each intention through a cvross validation test:


```
$ (Luci) make no_free_lunch
```

### Test the bot

The goal is give the models enough data to pass the test when executing:


```
$ (Luci) make test
```
