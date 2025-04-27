# Surfgram CLI

Modern Telegram bot framework's command line interface.

## Usage

| Command Format            | Description                          |
|---------------------------|--------------------------------------|
| surfgram [OPTIONS] COMMAND [ARGS]... | Main command to interact with the Surfgram CLI |

## Global Options

| Option        | Description                                      |
|---------------|--------------------------------------------------|
| --no-graphics | Disable ASCII banner display and all the graphics |
| --help        | Show this message and exit                         |

## Commands

### new

Create a new bot directory with template.

| Command Format            | Description                                    |
|---------------------------|------------------------------------------------|
| surfgram new [OPTIONS] BOT_NAME | Command to create a new bot directory          |

#### Options

| Option        | Description                                                                                          |
|---------------|------------------------------------------------------------------------------------------------------|
| --types TEXT | Template types to include: 'all', 'base', or specific types separated by commas (e.g., callback_queries,commands,configs,keyboards) [default: all] |
| --full-trace | Show full error traceback                                                                          |

#### Flow

| Step | Description                       |
|------|-----------------------------------|
| 1    | Prints creation header            |
| 2    | Prompts for bot token (hidden input) |
| 3    | Creates bot structure             |
| 4    | Shows success/error message       |

### delete

Delete the specified bot directory.

| Command Format            | Description                                   |
|---------------------------|-----------------------------------------------|
| surfgram delete [OPTIONS] BOT_NAME | Command to delete a specified bot directory |

#### Options

| Option        | Description                             |
|---------------|-----------------------------------------|
| --full-trace | Show full error traceback               |

#### Flow

| Step | Description                             |
|------|-----------------------------------------|
| 1    | Prints deletion header                  |
| 2    | Requests confirmation                   |
| 3    | Deletes bot directory                   |
| 4    | Shows success/cancel message            |

### run 

Run the specified bot.

| Command Format            | Description                                   |
|---------------------------|-----------------------------------------------|
| surfgram run [OPTIONS] | Command to run the specified bot             |

#### Required Options

| Option        | Description                              |
|---------------|------------------------------------------|
| --bot TEXT | Directory containing the bot commands    |
| --config TEXT | Config class in the bot directory        |
|---------------|------------------------------------------|
| --debug     | Enable debug mode                       |
| --on-reload | Automatically reload bot on changes     |
| --full-trace | Show full error traceback               |

#### Flow

| Step | Description                               |
|------|-------------------------------------------|
| 1    | Prints run header                         |
| 2    | Displays config status                    |
| 3    | Starts bot with specified configuration    |