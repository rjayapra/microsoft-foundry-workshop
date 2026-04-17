# my-work-assistant

Your AI-powered workspace assistant with custom skills for professional content creation.

## New Workshop Content

Hands-on workshop package for Azure Logic Apps autonomous agentic workflows is now available under the docs site content:

- docs/index.md
- docs/agenda.md
- docs/facilitator-guide.md
- docs/prerequisites.md
- docs/lab-00-environment-validation.md
- docs/lab-01-first-autonomous-agent.md
- docs/lab-02-debug-autonomous-agent.md
- docs/lab-03-connect-tools-external-services.md
- docs/lab-04-foundry-evaluation-and-automation.md
- docs/lab-05-end-to-end-scaleout-and-demos.md
- docs/lab-optional-mcp-tool-onboarding.md
- docs/troubleshooting.md
- docs/post-workshop.md

GitHub Pages workflow is included at:

- .github/workflows/github-pages.yml

## Available Skills

### 1. LinkedIn Article Writer

A comprehensive skill for transforming research topics into engaging LinkedIn articles optimized for maximum reach and engagement.

**Location:** `.copilot/skills/linkedin-article-writer/`

### 2. Knowledge Base Content Creator

Create customized articles, presentations, and learning materials tailored to your topic and audience's expertise level. Adapts content for technical professionals, business users, students, beginners, executives, or practitioners.

**Location:** `.copilot/skills/knowledge-base-creator/`

### 3. Code Sample Generator

Generate production-quality code samples, complete projects, and starter templates for any topic. Automatically adds code to your GitHub repository and integrates with your LinkedIn and Knowledge Base skills.

**Location:** `.copilot/skills/code-sample-generator/`

**Auto-Repository Integration:** ✅ Generated code is automatically committed and pushed to your repo!

### 4. Solution Architecture & Design Assistant

Transform customer use cases into comprehensive architectural solutions, design recommendations, and meeting-ready materials. Accelerates solution design with Azure-specific patterns, reference architectures, and best practices.

**Location:** `.copilot/skills/architecting-skill/`

## How to Use Skills

### Using the Code Sample Generator Skill

Generate code samples and complete projects that automatically get added to your repository.

#### Example Requests:

**Quick Code Snippet:**
```
"Generate a Python snippet showing how to call Azure OpenAI API and add it to the repo"
```

**Complete Project:**
```
"Create a chatbot project using Azure OpenAI with a web interface. Include deployment instructions and add to repository."
```

**Production Template:**
```
"Build a production-ready RAG system template with Azure AI Search, including infrastructure code, tests, and CI/CD pipeline. Add everything to the repo."
```

**Multi-Language Examples:**
```
"Create 'Hello Azure OpenAI' examples in Python, TypeScript, and C#. Add all three to the repository."
```

#### Repository Organization:

Generated code is automatically organized:

```
my-work-assistant/
├── samples/           # Quick snippets (< 50 lines)
├── projects/          # Complete projects (50-200+ lines)
├── templates/         # Production templates
└── guides/            # Documentation
```

#### What You Get:

- ✅ Production-quality code with comments
- ✅ README and setup instructions
- ✅ Tests (for projects and templates)
- ✅ Configuration files (.env.example, etc.)
- ✅ Automatic commit to your repository
- ✅ Proper .gitignore and dependencies

---

### Using the Knowledge Base Content Creator Skill

Create articles, presentations, or training materials that automatically adapt to your audience's expertise level.

#### Example Requests:

**For Technical Professionals:**
```
"Create a deep-dive article about Kubernetes networking for experienced DevOps engineers. Include architecture diagrams and performance optimization techniques."
```

**For Business Users:**
```
"Prepare a presentation about AI agents for new customers. Make it 15 slides with use cases and a hands-on demo walkthrough. Focus on business value and ROI."
```

**For Students:**
```
"Create a beginner's guide to machine learning for computer science students. Make it engaging with interactive exercises and real-world examples. About 2,000 words."
```

**For Executives:**
```
"Prepare a 7-slide executive presentation on cloud migration strategy. Focus on business impact, cost savings, and competitive advantage."
```

**For Practitioners:**
```
"Create a step-by-step implementation guide for setting up Azure private endpoints. Include all CLI commands, troubleshooting tips, and configuration examples."
```

#### What You'll Get:

The skill delivers different outputs based on your audience:

| Audience Type | Content Style | Depth | Hands-On | Engagement |
|---------------|---------------|--------|----------|------------|
| **Technical Pros** | Code-heavy, precise | 90% | Optional | Direct |
| **Business Users** | Value-focused | 40% | 50% | Demo-driven |
| **Students** | Interactive, fun | 60% | 70% | Gamified |
| **Beginners** | Analogy-rich | 20% | 60% | Patient |
| **Executives** | Strategic, concise | 30% | 0% | Data-driven |
| **Practitioners** | Step-by-step | 70% | 90% | Practical |

---

### Using the LinkedIn Article Writer Skill

Simply ask GitHub Copilot to help you write a LinkedIn article based on your research. Here are some examples:

#### Example 1: Basic Article Request
```
"I've been researching AI in healthcare. Can you help me write a LinkedIn article about my findings on how AI is improving early disease detection?"
```

#### Example 2: Specific Research Data
## 🚀 Quick Start Examples

### Scenario 1: Code + Article Combo
```
"Generate a Python script that uses Azure Computer Vision to analyze images. 
Write a LinkedIn article about it with code examples. 
Add the code to my repository."
```

**Result:**
- Working code in `/samples/azure-computer-vision/`
- LinkedIn article with embedded snippets
- GitHub link in the article
- All committed and pushed

### Scenario 2: Multi-Audience Content

#### Example 3: With Customization
```
"Write a LinkedIn article about my research on sustainable supply chains. Make it data-driven, focused on executives, and around 1,200 words. Use a professional but approachable tone."
```

#### Example 4: Multiple Topics
```
"I've been researching three trends in fintech: embedded finance, AI-driven fraud detection, and crypto regulation. Create a LinkedIn article that ties these together."
```

### What the Skill Will Provide

When you request a LinkedIn article, the skill will generate:

1. **Compelling Title** - Optimized for clicks and SEO
2. **Attention-Grabbing Hook** - First 2-3 lines that appear in feed preview
3. **Well-Structured Content** - Clear sections with subheadings
4. **Actionable Takeaways** - Practical insights readers can implement
5. **Engagement Prompt** - Question or CTA to drive comments
6. **Relevant Hashtags** - 3-5 hashtags for discoverability
7. **Publishing Tips** - Best times to post and engagement strategies

### Customization Options

You can customize your article by specifying:

- **Tone:** Formal, casual, technical, accessible
- **Length:** Quick read (500-800 words) or deep-dive (1,500+ words)
- **Audience:** Executives, managers, individual contributors, students
- **Focus:** Data-driven, story-driven, actionable, thought-provoking
- **Industry:** Tech, finance, marketing, healthcare, etc.

### Tips for Best Results

1. **Be Specific About Your Research**
   - Share key findings, statistics, or insights
   - Mention the context of your research
   - Explain why it matters to your audience

2. **Identify Your Target Audience**
   - Who are you trying to reach?
   - What level of expertise do they have?
   - What challenges are they facing?

3. **Provide 3ontext**
   Quick Start Examples

### Scenario 1: Multi-Audience Content
```
"I need to explain Azure AI Foundry to three different groups:
1. A technical article for cloud architects
2. A presentation for business stakeholders  
3. A beginner's guide for students
4
Create all three versions."
```

### Scenario 2: Workshop Preparation
```
"Create a 3-hour workshop on 'Introduction to GenAI' for new customers. Include:
- Presentation slides
- Hands-on lab exercises
- Facilitator guide
- Participant materials"
```

### Scenario 3: Quick Reference
```
"Create a one-page quick reference guide for Azure OpenAI best practices aimed at practitioners. Make it printable with common commands and troubleshooting tips."
```

### Scenario 5: Progressive Content
```
"Create a guide on microservices architecture with three depth levels:
- Executive overview (5 minutes read)
- Technical overview for developers (15 minutes)
- Deep dive implementation guide (45 minutes)"
```

## Tips for Best Results

### Be Specific About:
1. **Your Topic** - Clear, focused topic description
2. **Your Audience** - Technical level and role
3. **Format** - Article, presentation, workshop, guide
4. **Length** - Word count or slide count
5. **Special Needs** - Code examples, demos, analogies

### Example of a Complete Request:
```
TOPIC: Securing AI workloads with private endpoints
AUDIENCE: Technical professionals (cloud architects)
FORMAT: Technical article
LENGTH: 2,500 words
DEPTH: Deep dive with implementation details
SPECIAL REQUIREMENTS: Include Bicep templates, network diagrams, and security best practices
```

## 🎨 Combining Skills (The Power Move!)

You can use multiple skills together to create complete content packages:

### Example 1: Complete Technical Content Package
```
"I'm researching Azure AI Agents. Create:
1. A working Python agent example (Code Generator)
2. A technical guide for developers (Knowledge Base)
3. A LinkedIn article announcing the work (LinkedIn Writer)
All code should be added to my repository."
```

**You'll Get:**
- `/projects/azure-ai-agent/` with complete code → committed to GitHub
- `/guides/azure-ai-agents-developer-guide.md` → technical documentation
- LinkedIn article with links to your GitHub repo
- Everything cross-referenced and ready to publish!

### Example 2: Workshop Material Creation
```
"Create a 3-hour workshop on Azure OpenAI for students:
1. Presentation slides (Knowledge Base)
2. 3 hands-on coding exercises with solutions (Code Generator)
3. Setup guide and examples
Add all code to repository."
```

**You'll Get:**
- Workshop presentation in `/guides/`
- Three complete coding projects in `/projects/workshop-exercises/`
- All code committed to GitHub
- Ready-to-run workshop materials

### Example 3: Research to Production
```
"I've been researching RAG systems with Azure AI Search. Create:
1. A production-ready RAG template (Code Generator)
2. A technical implementation guide (Knowledge Base)
3. A LinkedIn article about my findings (LinkedIn Writer)
Include infrastructure code and deployment steps."
```

**You'll Get:**
- `/templates/production-rag-system/` with complete codebase
- Infrastructure as Code (Bicep/Terraform)
- Technical documentation
- LinkedIn article
- Everything in your GitHub repo with proper organization

## Support

If you need help or want to refine the skillsto explore?

4. **Request Revisions**
   - Ask for a different hook or tone
   - Request more data or examples
   - Ask for length adjustments

## Adding More Skills

To add additional custom skills:

1. Create a new folder in `.copilot/skills/`
2. Add a `SKILL.md` file with detailed instructions
3. Update this README with usage examples

## Examples

### Example Interaction

**You:**
"I've been researching machine learning model optimization. I found that quantization can reduce model size by 75% while maintaining 95% accuracy. Write a LinkedIn article about this for ML engineers."

**Copilot will:**
1. Read the LinkedIn Article Writer skill
2. Generate a compelling hook about efficiency gains
3. Structure the article with technical depth appropriate for ML engineers
4. Include your specific findings (75% size reduction, 95% accuracy)
5. Add practical implementation tips
6. Conclude with engagement prompt
7. Suggest relevant hashtags like #MachineLearning #MLOps #AI

### Another Example

**You:**
"Create a LinkedIn article about my research on developer productivity. Focus on these findings: developers spend 40% of time on meetings, only 25% coding, and async tools can reclaim 10+ hours per week. Make it punchy and aimed at engineering leaders."

**Copilot will:**
1. Create a hook highlighting the shocking 25% coding time stat
2. Structure the article with your three key data points
3. Use a tone that resonates with engineering leaders
4. Provide actionable recommendations for implementation
5. Include takeaways about meeting reduction and async adoption
6. End with a thought-provoking question about team efficiency

## Support

If you need help or want to refine the skill, just ask GitHub Copilot in natural language!