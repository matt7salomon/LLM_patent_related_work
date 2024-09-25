# LLM_patent_related_work


# Patent Novelty and Obviousness Checking with Multiple Data Sources

## Dataset and API Information:
This version allows you to choose between various patent data sources:
- **Lens.org**: API-based patent search, requires API key.
- **USPTO Bulk Data**: Public patent data from the US Patent Office, no key required.
- **Google Patents**: Requires a Google Cloud Project for BigQuery.
- **WIPO Patentscope**: Global patent search, requires API key.

## Patent Search Function
The `search_patents()` function selects the appropriate data source based on the flag set at the beginning of the code.

## Prior Art Retrieval
The `retrieve_prior_art()` function uses the selected API to pull related patents for comparison.

## Similarity Calculation using LLMs
We use a pre-trained Hugging Face model for semantic similarity and calculate cosine similarity using TF-IDF vectors.

## Novelty Check Pipeline
The `patent_novelty_check()` function brings it all together, helping us check the novelty of a new patent claim against prior art from different data sources.


# Patent claim generator code:

## Explanation:

**Function `analyze_patent_claims_for_suggestions()`:** 
This function takes the extracted patent claims and uses GPT-4 to suggest ways to broaden or narrow the claims.
It prompts GPT-4 to act as a patent expert and provides suggestions for improving the claims.

**Function `upload_and_analyze_patent_claims()`:**
This function simulates reading a patent document (in this case, a .txt file with the claims), and it passes the claims to GPT-4 for analysis.
The uploaded file should contain claims in plain text for GPT-4 to analyze.

**Pipeline `patent_claim_suggestion_pipeline()`:**
This pipeline coordinates the process by uploading the claims, analyzing them, and returning suggestions.

### Steps:
Upload Patent Claims: The patent claims can be uploaded as a .txt file. You can modify this to handle other formats (e.g., PDFs) if needed.
Analyze with GPT-4: GPT-4 will suggest ways to either broaden or narrow the claims to improve the likelihood of patent approval and the scope of protection.

### Example Workflow:
Place the patent claims in a text file (e.g., patent_claims.txt).
Run the patent_claim_suggestion_pipeline(file_path) with the path to the file.
GPT-4 will analyze the claims and suggest improvements based on its understanding of the claims and potential strategies for approval.


# Patent licensing and value evaluation code:

### **What is the Goal of this Code?**
This code helps us **analyze a patent** (which is like a special ownership document for an invention) to find **business opportunities**. It uses a really smart computer program (called GPT-4) to figure out where we could sell or license the invention or how valuable the invention is based on what’s happening in the market right now (what people want to buy).

---

### **How Do We Use This Code?**
- You give it **patent claims** (descriptions of your invention).
- You tell it about **market trends** (what's popular or in demand in the world right now).
- The smart computer program (GPT-4) will think about where this invention could be useful and how valuable it might be.

---

### **The Functions:**

#### 1. **Timer Decorator (`timer_decorator`)**
   ```python
   def timer_decorator(func):
       def wrapper(*args, **kwargs):
           start_time = time.time()
           result = func(*args, **kwargs)
           end_time = time.time()
           print(f"Function '{func.__name__}' took {end_time - start_time:.4f} seconds")
           return result
       return wrapper
   ```
   **What It Does:**
   - This is like a stopwatch.
   - Every time we run a function (like asking GPT-4 for help), it measures how long it takes for the function to finish.
   - It then prints out, "This function took X seconds."

#### 2. **Analyzing Patent Claims for Licensing Opportunities (`analyze_patent_value_and_opportunities`)**
   ```python
   @timer_decorator
   def analyze_patent_value_and_opportunities(claims, market_data, patent_applications):
       ...
   ```
   **What It Does:**
   - This is the smart function that asks GPT-4 to help us figure out how valuable the invention is and where we can use it in the market.
   - **Inputs**: 
     - **Claims**: This is like a list of things the invention does (its powers or abilities).
     - **Market Data**: Information about what’s popular right now, like "people are buying more electric cars" or "AI is being used in healthcare."
     - **Applications**: Ways that the invention could be used, like "this technology can improve smart cars" or "this tool can be used in medical machines."
   - GPT-4 then gives us **suggestions** on where to license the invention (sell the right to use it) and how valuable it is.

#### 3. **Upload and Analyze Patent for Licensing (`upload_and_analyze_patent_for_licensing`)**
   ```python
   @timer_decorator
   def upload_and_analyze_patent_for_licensing(file_path, market_data, patent_applications):
       ...
   ```
   **What It Does:**
   - This function takes a **patent file** (like a text document with the patent details) from your computer.
   - It reads the file, grabs the **claims** inside, and sends them to GPT-4 for suggestions on licensing and value.
   - Basically, it reads your invention's description and then asks GPT-4 for advice based on market data and applications.

#### 4. **Main Pipeline for Licensing and Value Analysis (`patent_licensing_opportunities_pipeline`)**
   ```python
   @timer_decorator
   def patent_licensing_opportunities_pipeline(file_path, market_data, patent_applications):
       ...
   ```
   **What It Does:**
   - This is the **boss function** that coordinates everything.
   - You give it a **patent file** (your invention's description), **market data** (what's popular right now), and **potential applications** (where this invention could be used).
   - This function runs all the steps: 
     1. It reads the patent file.
     2. It analyzes the claims and looks for licensing opportunities.
     3. It gives you GPT-4’s suggestions on how to make money from your invention and how valuable it might be.

#### 5. **Example Usage (How to Use the Code)**
   ```python
   file_path = "/path/to/your/patent_claims.txt"
   market_data = "..."
   patent_applications = "..."
   patent_licensing_opportunities_pipeline(file_path, market_data, patent_applications)
   ```
   **What It Does:**
   - Here’s how you use everything:
     - **file_path**: This is where you upload your patent document. It's a file that describes your invention.
     - **market_data**: You give some information about what’s going on in the world right now—what people are buying or interested in.
     - **patent_applications**: You give examples of where your invention might be useful.
   - The `patent_licensing_opportunities_pipeline` function will then tell you what GPT-4 thinks about your invention and how you can use it to make money!

---

### **How Does GPT-4 Help?**
GPT-4 is like a super-smart assistant:
- It reads the **patent claims** (the abilities of your invention).
- It looks at the **market trends** and figures out what’s popular.
- It tells you, “Hey, your invention could be really valuable in this area” or “You could sell the right to use this invention to this company.”
- It helps you understand if your invention is **valuable** and **where** it can be used.

### **What’s the Result?**
After you run the code:
- GPT-4 gives you **suggestions** about how you can license your invention or where to sell it.
- It also helps you figure out how much your invention might be worth based on what’s happening in the world right now.


