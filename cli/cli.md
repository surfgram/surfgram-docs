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
