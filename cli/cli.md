# **Surfgram CLI Documentation**  

## **Overview**  
The **Surfgram CLI** is the official command-line interface for managing Telegram bots built with the **Surfgram framework**. It provides tools for:  
- **Creating** new bot projects  
- **Deleting** existing bots  
- **Running** bots 

> **⚠️ Important:**  
> This CLI is the **recommended way** to interact with the Surfgram framework.  
> Avoid manual bot setup — use the CLI for best practices.  

---

## **Installation**  
Ensure `surfgram` is installed, then run:  
```bash
surfgram --help
```  
This displays all available commands.  

---

## **Commands**  

### **1. `surfgram new` – Create a New Bot**  
**Usage:**  
```bash
surfgram new <bot_name> [OPTIONS]
```  

#### **Options**  
| Option | Description | Default |
|--------|-------------|---------|
| `--full-trace` | Show complete error traces (debugging) | `False` |  

#### **Example**  
```bash
surfgram new my_telegram_bot
```  

---

### **2. `surfgram delete` – Remove a Bot**  
**Usage:**  
```bash
surfgram delete <bot_name> [OPTIONS]
```  

#### **Options**  
| Option | Description | Default |
|--------|-------------|---------|
| `--full-trace` | Show complete error traces (debugging) | `False` |  

#### **Example**  
```bash
surfgram delete old_bot
```  

---

### **3. `surfgram run` – Start the Bot**  
**Usage:**  
```bash
surfgram run [OPTIONS]
```  

#### **Key Options**  
| Option | Description | Default |
|--------|-------------|---------|
| `--bot` / `-b` | Specify bot directory (default: current) | `None` |
| `--config` / `-c` | Manually set config (e.g., `my_module.ProdConfig`) | Auto-detected |
| `--debug` | Enable debug logging | `False` |
| `--autoreload` | Auto-restart on file changes (dev mode) | `False` |
| `--full-trace` | Show complete error traces | `False` |

#### **Examples**  
**Production:**  
```bash
surfgram run
```  

**Development:**  
```bash
surfgram run --debug --autoreload
```  

---

## **Global Options**  
All commands support:  
| Option | Description |  
|--------|-------------|  
| `--no-graphics` | Disable ASCII art and styling (useful for CI/CD) |  

---

## **Error Handling**  
- **User-friendly messages** (avoids raw stack traces by default).  
- **Debug mode** (`--full-trace`) for detailed error inspection.  

---

## **Best Practices**  
✔ **Use `--autoreload` during development** – Faster iterations.  
✔ **Avoid manual config edits** – Let the CLI handle setup.  
✔ **Enable `--debug` when troubleshooting** – More verbose logs.  

---

## **Example Workflow**  
1. **Create a bot:**  
   ```bash
   surfgram new my_bot
   ```  
2. **Enter your bot token (hidden input).**  
3. **Run in dev mode:**  
   ```bash
   cd my_bot
   surfgram run --debug --autoreload
   ```  
4. **Deploy to production:**  
   ```bash
   surfgram run --config config.ProdConfig
   ```  

---

### **Need Help?**  
Run:  
```bash
surfgram --help
```  
=======
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
