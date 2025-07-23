# 🚀 Creating AI Agents with Modelfiles - Super Easy!

This is way easier than importing JSON files! Think of Modelfiles like recipes that tell Open WebUI how to make your custom AI agents.

## 🎯 What You'll Get

3 awesome AI agents:
- 🧙‍♂️ **Cover Letter Pipeline** (uses your llama3.3:70b)
- 🕵️‍♀️ **Fact Checker** (uses your phi4:latest)  
- 🤖 **Human Sound Checker** (uses your deepseek-r1:8b)

## 📁 Your Modelfiles

I created these files for you:
- `Modelfile-pipeline` - Main cover letter creator
- `Modelfile-fact-checker` - Truth detective
- `Modelfile-human-checker` - Human-like scorer

## 🎮 Super Easy Steps

### Step 1: Open Your Terminal/Command Prompt
- **Mac**: Press Cmd+Space, type "Terminal", press Enter
- **Windows**: Press Win+R, type "cmd", press Enter
- **Linux**: Press Ctrl+Alt+T

### Step 2: Navigate to Your Files
```bash
cd /Users/smaq-daddy/repos/cover-letter-genie
```

### Step 3: Create Your First Agent (Pipeline)
```bash
ollama create cover-letter-pipeline -f Modelfile-pipeline
```

You should see: ✅ `success`

### Step 4: Create Your Fact Checker
```bash
ollama create fact-checker -f Modelfile-fact-checker
```

You should see: ✅ `success`

### Step 5: Create Your Human Checker
```bash
ollama create human-checker -f Modelfile-human-checker
```

You should see: ✅ `success`

### Step 6: Check They Were Created
```bash
ollama list
```

You should now see your new models:
- `cover-letter-pipeline:latest`
- `fact-checker:latest`
- `human-checker:latest`

## 🌐 Using Them in Open WebUI

1. **Open your Open WebUI** in the browser
2. **Look for the model dropdown** (usually top of chat)
3. **You should see your new models:**
   - Cover Letter Pipeline
   - Fact Checker  
   - Human Checker

## 🎯 Test Your Agents

### Test the Pipeline Agent:
```
Select: cover-letter-pipeline
Type: "Hi! Help me create a cover letter for a marketing job"
```

### Test the Fact Checker:
```
Select: fact-checker  
Type: "Check this: I have 10 years experience as CEO of Google"
```

### Test the Human Checker:
```
Select: human-checker
Type: "Score this letter: Dear Sir, I am writing to apply for position..."
```

## 🛠️ If Something Goes Wrong

### Problem: "ollama command not found"
**Fix:** Make sure Ollama is installed and running

### Problem: "model not found" when creating
**Fix:** 
1. Check that the base model exists: `ollama list`
2. Make sure you're in the right folder with the Modelfiles

### Problem: Models don't appear in Open WebUI
**Fix:**
1. Refresh your browser
2. Restart Open WebUI
3. Check that Ollama is connected to Open WebUI

### Problem: Terminal says "file not found"
**Fix:**
1. Make sure you're in the right directory: `pwd`
2. List files to confirm: `ls -la`
3. Check the Modelfile names are correct

## 🎨 Customizing Your Agents

You can edit the Modelfiles to:

### Change the Base Model:
```
FROM mistral:7b  # Use a different model
```

### Adjust Settings:
```
PARAMETER temperature 0.5  # Make more/less creative
PARAMETER top_p 0.7       # Change response style
```

### Modify the Personality:
Edit the `SYSTEM` section to change how they behave.

## 🏆 Why This Method Works Better

✅ **More Reliable** - Modelfiles are the native way  
✅ **Uses Your Local Models** - Leverages what you already have  
✅ **Easier to Edit** - Just text files you can modify  
✅ **Better Performance** - Optimized for your specific models  
✅ **No Import Issues** - Works with all Open WebUI versions  

## 🎪 Advanced Tips

### Create Aliases for Easy Access:
```bash
# Create shortcuts
echo 'alias create-pipeline="ollama create cover-letter-pipeline -f Modelfile-pipeline"' >> ~/.bashrc
```

### Update Your Agents:
```bash
# When you modify a Modelfile, recreate the model
ollama create cover-letter-pipeline -f Modelfile-pipeline
```

### Delete and Recreate:
```bash
# Remove old version
ollama rm cover-letter-pipeline
# Create new version  
ollama create cover-letter-pipeline -f Modelfile-pipeline
```

## 🎉 You Did It!

Now you have professional AI agents that:
- Use your powerful local models
- Work reliably every time
- Can be easily customized
- Integrate perfectly with Open WebUI

Much better than trying to import JSON files! 🚀
