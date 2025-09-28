# Marketplace Validator

Validate credit card and loan listings against Marketplace Standards using Google Gemini LLMs. The notebook automates the validation workflow, produces structured outputs, and evaluates performance.

## 🚀 Features
- Load sample lender listings from `.txt` files.  
- Run a **Validator LLM** to check compliance with marketplace standards.  
- Generate structured JSON outputs per listing.  
- Use a **Judge LLM** to score validator responses.  
- Aggregate results into:
  - **`.csv`** → pass rate & criterion scores.  
  - **`.json`** → per-listing validation details.  
- Compare different prompt versions for effectiveness.

## 📂 Project Structure
```
marketplace_validator.ipynb     # Main notebook
prompts/
  marketplace_validator_prompt.txt
  judge_prompt.txt
  improved_marketplace_validator_prompt.txt
data/
  sample_listings/              # Input lender listing text files
  validation_original_prompt/   # Results from first validation run
  validation_improved_prompt/   # Results from improved prompt 
  reporting/
    leaderboard.csv                 # Aggregated scores (output)
    details.json                    # Detailed run results (output)
```

## ⚙️ Requirements
Install dependencies before running:
```bash
pip install google-genai pandas tqdm python-dotenv
```

## 🔑 Setup
1. Get a Google Gemini API key.  
2. Set it as an environment variable:
   ```bash
   export GEMINI_API_KEY="your_api_key_here"
   ```
   Or inside the notebook:
   ```python
   os.environ["GEMINI_API_KEY"] = "your_api_key_here"
   ```

## ▶️ Usage
1. Open `marketplace_validator.ipynb` in Jupyter.  
2. Update paths in the **Config** section if needed
3. Run all cells:
   - Listings will be validated.  
   - Results will be stored in `data/validation_original_prompt/`.  
   - Leaderboard and details files will be generated.  

## 📊 Outputs
- **Leaderboard (`.csv`)**: Summary table with pass rate and criterion scores.  
- **Details (`.json`)**: Structured record of each listing, standards, and AI response.  

## 🛠️ Extending
- Replace `prompts/marketplace_validator_prompt.txt` with an improved prompt to test new strategies.  
- Add more sample listings under `data/sample_listings/`.  
- Change the `MODEL` in config to try different Gemini variants.  
