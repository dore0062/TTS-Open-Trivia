# TTS-Open-Trivia
https://opentdb.com/

A simple library to retrieve trivia questions from Open Trivia Database with Tabletop Simulator scripting. Use a session code to prevent duplicate trivia questions from appearing. Please read the webpage above for limitations.


## Usage:
### Example code:
```lua
openTrivia = require("opentrivia")

function onLoad()
  -- openTrivia:categoryLookup()

  local parameters = {
    difficulty="easy"
  }

  openTrivia:getToken(function(token)
    parameters.token = token
    openTrivia:getQuestions(1, doThing(results), parameters)
  end)
end

function doThing(results)
  log(results)
end
```

## Commands:
### openTrivia:getToken(callbackFunction)
Returns a randomly generated session token string to a callback function. 

### openTrivia:getQuestions(number, callbackFunction, parameters)
Returns a table of questions based on parameters given. False if error. All parameters are optional.

#### Parameters:
|  Variable  |         options        |
|:----------:|:----------------------:|
| difficulty | "easy","medium","hard" |
| token      | string                 |
| category   | num                    |
| type       | "boolean","multiple"   |

### openTrivia:categoryLookup()
Logs category id numbers

### openTrivia:resetSession(token, cb)
Resets the session with the given token ID, returns false if error
