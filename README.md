⚡ HTML Quick-Styler
AI-Powered HTML Page Generator with IBM Granite 3.3 2B Instruct

Truly AI-based website generation — IBM Granite 3.3 2B writes the entire HTML, CSS, and content from scratch. No hardcoded templates. No placeholder text. Just pure AI.


📌 Table of Contents

Project Overview
Key Features
Four Core Scenarios
Tech Stack
Architecture
Prerequisites
Installation & Setup
How to Run on Google Colab
Project Structure
How It Works
AI vs Script Breakdown
Token Usage & Speed
Color Palette Options
Gradio Interface Tabs
Performance Optimization
Troubleshooting
Future Improvements
Credits


📖 Project Overview
HTML Quick-Styler is an intelligent, fully AI-driven web page generation platform built on IBM Granite 3.3 2B Instruct. Unlike traditional website builders that use fixed templates, HTML Quick-Styler lets the AI write the entire HTML file, all CSS styling, all animations, and all page content from a simple text description.
User types:    "A SaaS platform for project management"
Granite writes: Complete HTML + CSS + JS website in ~2 minutes
Deployed through a Gradio interface on Google Colab — accessible to anyone with a Google account. No local setup required.

✨ Key Features

100% AI Generated — IBM Granite writes every line of HTML and CSS
Zero Templates — No hardcoded layouts or placeholder text
8 Color Themes — modern, vibrant, ocean, forest, sunset, luxury, creative, minimal
Auto Section Detection — AI decides which sections your page needs
Live Preview — Instantly render the generated page inside Gradio
Production Ready — Clean, responsive, SEO-optimized HTML output
Fast Generation — Optimized to complete under 2-3 minutes
5-Tab Gradio UI — Generate, Preview, Palettes, Templates, Guide
Mobile Responsive — Every generated page works on all screen sizes
Dark Theme — Modern glassmorphism design style throughout


🎯 Four Core Scenarios
Scenario 1 — Portfolio Website
Who: Freelance designers wanting a fast professional portfolio
AI Generates:

Hero section with strong CTA
Responsive portfolio gallery grid
Professional about and bio section
Client testimonials with star ratings
Validated contact form
Social media footer

Example Input:
Title:       Alex Design Studio
Description: Hero with welcome message, portfolio gallery with 6 items,
             about section, client testimonials, contact form, footer
Style:       vibrant

Scenario 2 — SaaS Landing Page
Who: Startups launching a new product
AI Generates:

Hero banner with value proposition
Features showcase with emoji icons
3-tier pricing comparison table
Social proof testimonials
Conversion-optimized CTA buttons
Professional footer

Example Input:
Title:       LaunchPad SaaS
Description: Hero with value proposition, features showcase,
             pricing plans, testimonials, CTA buttons, footer
Style:       modern

Scenario 3 — Corporate Website
Who: Companies needing a professional web presence
AI Generates:

Sticky navbar with company branding
Mission, vision, and values section
Services grid layout
Team member profiles
Contact and inquiry form
Footer with privacy policy

Example Input:
Title:       Nexus Corporation
Description: Company overview, mission and vision, services grid,
             team members, contact form, footer with privacy policy
Style:       minimal

Scenario 4 — Color Palette Explorer
Who: Designers finding their visual identity
AI Generates:

Full website preview in chosen color theme
Hex codes for every color component
Consistent color across all elements
Dark theme optimized backgrounds

Example Input:
Title:       My Brand
Description: Creative agency website with portfolio and services
Style:       luxury   ← try all 8 options

🛠️ Tech Stack
TechnologyPurposePython 3.8+Core backend logicIBM Granite 3.3 2B InstructAI HTML/CSS generationGradioInteractive web interfaceHuggingFace TransformersModel loading and inferencePyTorch (float16)GPU accelerationGoogle ColabCloud deploymentHTML5 / CSS3Output formatAccelerateOptimized model loading

🏗️ Architecture
┌──────────────────────────────────────┐
│           USER INPUT                 │
│   Title + Description + Style        │
└──────────────┬───────────────────────┘
               │
               ▼
┌──────────────────────────────────────┐
│         GRADIO INTERFACE             │
│  Generate | Preview | Palettes       │
│  Templates | Guide                   │
└──────────────┬───────────────────────┘
               │
               ▼
┌──────────────────────────────────────┐
│      PYTHON ORCHESTRATION            │
│  • Builds prompt from user input     │
│  • Calls IBM Granite model           │
│  • Cleans HTML response              │
│  • Returns to Gradio display         │
└──────────────┬───────────────────────┘
               │
               ▼
┌──────────────────────────────────────┐
│    IBM GRANITE 3.3 2B INSTRUCT       │
│                                      │
│  Writes: ✅ All HTML structure       │
│          ✅ All CSS styling          │
│          ✅ All animations           │
│          ✅ All page content         │
│          ✅ All section layouts      │
│          ✅ Responsive queries       │
│          ✅ Color scheme             │
└──────────────┬───────────────────────┘
               │
               ▼
┌──────────────────────────────────────┐
│       PRODUCTION HTML OUTPUT         │
│  Complete file — deploy anywhere     │
└──────────────────────────────────────┘

📋 Prerequisites
Software:

Google Account (for Colab)
Modern browser (Chrome recommended)
Internet connection

Knowledge:

Basic Python (helpful)
Google Colab familiarity
HTML/CSS basics (optional)

Hardware — all provided by Colab:

GPU: T4 free tier or A100 Pro
RAM: 12GB+ auto-provided
Storage: 10GB+ for model weights


🚀 Installation & Setup
Step 1 — Open Google Colab
Visit colab.research.google.com → New Notebook
Step 2 — Enable GPU
Runtime → Change runtime type → GPU (T4) → Save
Step 3 — Install Packages
python!pip install -q gradio transformers torch accelerate sentencepiece
Step 4 — Load IBM Granite
pythonfrom transformers import AutoTokenizer, AutoModelForCausalLM
import torch

MODEL_ID = "ibm-granite/granite-3.3-2b-instruct"
tokenizer = AutoTokenizer.from_pretrained(MODEL_ID)
model = AutoModelForCausalLM.from_pretrained(
    MODEL_ID,
    torch_dtype=torch.float16,
    device_map="auto"
)
model.eval()
print("✅ IBM Granite 3.3 2B loaded!")
```

### Step 5 — Run All Cells in Order
Cells 1 through 6. Gradio launches automatically.

### Step 6 — Get Your Public URL
```
✅ Running on public URL: https://xxxxxxxx.gradio.live
```
Share this with anyone. Active for 72 hours.

---

## 📁 Project Structure
```
html_quick_styler.py
│
├── Cell 1 — Install dependencies
├── Cell 2 — Load IBM Granite + ask_granite()
├── Cell 3 — Color style hints dictionary
├── Cell 4 — truly_ai_generate() main function
├── Cell 5 — Gradio 5-tab interface
└── Cell 6 — demo.launch(share=True)

⚙️ How It Works
The entire generation happens in one function:
pythondef truly_ai_generate(title, description, style):

    # Step 1 — Build prompt (Python)
    system = "You are a senior web developer. Write complete HTML..."
    user   = f"Build: {title}. About: {description}. Style: {style}..."

    # Step 2 — Granite writes EVERYTHING (AI)
    response = ask_granite(system, user, max_tokens=3500)

    # Step 3 — Clean response (Python)
    html = response.strip()
    if "```html" in html:
        html = html.split("```html")[1].split("```")[0]

    return html, "✅ Done!"
IBM Granite writes every tag, every style, every word. Python just sends the request and cleans the output.

🤖 AI vs Script Breakdown
ComponentWho Writes ItHTML structure and tags✅ IBM GraniteCSS styling and variables✅ IBM GraniteAnimations and hover effects✅ IBM GraniteHero headline and copy✅ IBM GraniteFeature names and descriptions✅ IBM GraniteTestimonial quotes✅ IBM GranitePricing tiers✅ IBM GraniteTeam bios✅ IBM GraniteColor decisions✅ IBM GraniteMedia queries✅ IBM GraniteModel loading🐍 PythonPrompt building🐍 PythonResponse cleaning🐍 PythonGradio display🐍 Python
AI: ~95% | Python: ~5%

⏱️ Token Usage & Speed
GPUTimeT4 Free Colab2-3 minutes ✅A100 Colab Pro45-60 seconds ⚡V1001.5-2 minutes ✅
max_tokensTimeQuality40965-6 min⭐⭐⭐⭐⭐35002-3 min ✅⭐⭐⭐⭐⭐20001-2 min⭐⭐⭐⭐1000<1 min⭐⭐⭐
Recommended: max_tokens=3500 — best balance of speed and quality.

🎨 Color Palette Options
StylePrimaryBest Formodern#667eeaTech, SaaS, AIvibrant#ff6b6bCreative, Portfolioocean#4facfeCorporate, Financeforest#43e97bEco, Healthsunset#f7971eFood, Travelluxury#c9a96eFashion, Premiumcreative#9b59b6Design, Agencyminimal#2c3e50Professional

🖥️ Gradio Interface Tabs
TabWhat It Does⚡ GenerateEnter title, description, style → AI generates HTML👁️ PreviewRenders the generated page live🎨 PalettesBrowse all 8 color schemes with hex codes📋 TemplatesOne-click load for Portfolio, SaaS, Corporate📖 GuideFull how-to guide inside the app

⚡ Performance Optimization
python# These 3 settings give the fastest generation:

# 1. float16 when loading
torch_dtype=torch.float16

# 2. Optimized generation params
model.generate(
    max_new_tokens=3500,
    top_k=40,
    use_cache=True,
    temperature=0.7,
    top_p=0.85,
)

# 3. No-grad context
with torch.no_grad():
    outputs = model.generate(...)

🔧 Troubleshooting
ProblemCauseFixCUDA out of memoryGPU RAM fullRuntime → Factory resetIncomplete HTMLmax_tokens too lowIncrease to 3500Gradio link expired72hr limitRe-run last cellOutput has markdownModel added code blockHandled by cleaning codeGeneration >5 minCPU instead of GPUChange runtime to GPU

🚀 Future Improvements

JavaScript interactivity generation
Custom hex color picker
Multi-page website generation
Image embedding and suggestions
Export as ZIP file
React/Vue component output
Hugging Face Spaces permanent hosting
A/B variant generation


👥 Credits
AI ModelIBM Granite 3.3 2B InstructModel SourceHuggingFaceUI FrameworkGradioCloud PlatformGoogle ColabProject BySmartBridge × Skill Wallet
