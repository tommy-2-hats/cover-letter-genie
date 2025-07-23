# Multi-Agent Systems in Open WebUI

This guide shows you how to create intelligent agent systems that can route tasks to specialized models, eliminating the need to constantly switch between different models for different purposes.

## 🎯 Concept: Single Interface, Multiple Specialists

Instead of manually choosing different models for different tasks, create a **coordinator agent** that:
- Analyzes your request
- Routes to the appropriate specialist model
- Coordinates between multiple models when needed
- Provides unified responses

## 🏗️ Implementation Approaches

### Approach 1: Single Model Router (Recommended for Open WebUI)

Create one smart model that simulates multiple agents and handles routing internally.

**Advantages:**
- Works within Open WebUI's current architecture
- Single conversation thread
- No manual model switching
- Consistent context across "agents"

**Example Configuration:**
```json
{
  "id": "career-multi-agent",
  "name": "Career Multi-Agent System",
  "base_model_id": "gpt-4-turbo",
  "params": {
    "system": "You are a multi-agent coordinator managing specialized career assistants..."
  }
}
```

### Approach 2: Function-Based Routing (Advanced)

Use function calling to route to different model endpoints.

**Advantages:**
- Actually uses different models
- True specialization
- Can leverage model-specific strengths

**Requirements:**
- Open WebUI with function calling support
- API access to multiple models
- Custom function definitions

### Approach 3: Workflow Pipelines

Create sequential workflows that pass tasks between models.

**Advantages:**
- Clear task separation
- Optimized model selection
- Structured outputs

**Use Cases:**
- Resume analysis → Cover letter generation
- Company research → Interview prep
- Salary research → Negotiation strategy

## 🚀 Ready-to-Use Agent Configurations

### 1. Career Multi-Agent System
*Routes career tasks to specialized virtual agents*

```json
{
  "id": "career-multi-agent",
  "name": "Career Multi-Agent System",
  "meta": {
    "description": "Routes tasks to specialized career agents",
    "version": "1.0.0"
  },
  "base_model_id": "gpt-4-turbo",
  "params": {
    "system": "You are the Career Multi-Agent Coordinator managing:\n\n🎯 COVER_LETTER_AGENT - Cover letter writing\n📄 RESUME_AGENT - Resume optimization\n💼 INTERVIEW_AGENT - Interview preparation\n💰 SALARY_AGENT - Compensation analysis\n🔍 RESEARCH_AGENT - Company research\n\nWhen users ask for help, route to the appropriate agent and provide specialized responses.",
    "temperature": 0.8,
    "max_tokens": 2000
  }
}
```

### 2. Content Creation Hub
*Routes writing tasks to specialized content agents*

```json
{
  "id": "content-creation-hub",
  "name": "Content Creation Hub",
  "meta": {
    "description": "Multi-agent system for various content creation needs",
    "version": "1.0.0"
  },
  "base_model_id": "gpt-4",
  "params": {
    "system": "You coordinate specialized content creation agents:\n\n✍️ COPYWRITER - Marketing copy, ads, sales content\n📱 SOCIAL_MEDIA_AGENT - Posts, captions, hashtags\n📧 EMAIL_AGENT - Email campaigns, newsletters\n📝 BLOG_AGENT - Articles, SEO content\n🎥 SCRIPT_AGENT - Video scripts, presentations\n\nAnalyze requests and route to the best specialist.",
    "temperature": 0.9,
    "max_tokens": 1500
  }
}
```

### 3. Technical Consultant Network
*Routes technical questions to appropriate specialists*

```json
{
  "id": "tech-consultant-network",
  "name": "Technical Consultant Network",
  "meta": {
    "description": "Multi-agent system for technical consulting and problem-solving",
    "version": "1.0.0"
  },
  "base_model_id": "gpt-4-turbo",
  "params": {
    "system": "You manage a network of technical specialists:\n\n💻 DEVELOPER_AGENT - Code review, architecture, debugging\n🔧 DEVOPS_AGENT - Infrastructure, deployment, monitoring\n🛡️ SECURITY_AGENT - Security audits, best practices\n📊 DATA_AGENT - Analytics, databases, data science\n🎨 UX_AGENT - User experience, design systems\n\nRoute technical questions to the most qualified specialist.",
    "temperature": 0.7,
    "max_tokens": 2000
  }
}
```

### 4. Business Strategy Council
*Routes business questions to specialized advisors*

```json
{
  "id": "business-strategy-council",
  "name": "Business Strategy Council",
  "meta": {
    "description": "Multi-agent system for comprehensive business consulting",
    "version": "1.0.0"
  },
  "base_model_id": "gpt-4",
  "params": {
    "system": "You coordinate business strategy specialists:\n\n📈 MARKETING_STRATEGIST - Growth, campaigns, positioning\n💼 OPERATIONS_CONSULTANT - Process optimization, efficiency\n💰 FINANCIAL_ADVISOR - Budgeting, forecasting, investment\n👥 HR_SPECIALIST - Hiring, culture, management\n⚖️ LEGAL_ADVISOR - Compliance, contracts, risk\n\nRoute business questions to the appropriate expert council member.",
    "temperature": 0.8,
    "max_tokens": 1800
  }
}
```

## 🛠️ Advanced Implementation: Function-Based Routing

For true multi-model routing, you can use function calling (if supported):

```json
{
  "id": "true-multi-agent",
  "name": "True Multi-Agent System",
  "base_model_id": "gpt-4-turbo",
  "params": {
    "system": "You are an agent coordinator. Use the available functions to route tasks to specialized models.",
    "functions": [
      {
        "name": "route_to_specialist",
        "description": "Route a task to a specialized model",
        "parameters": {
          "type": "object",
          "properties": {
            "specialist": {
              "type": "string",
              "enum": ["cover_letter", "resume", "interview", "salary", "research"]
            },
            "task": {
              "type": "string",
              "description": "The specific task to perform"
            },
            "context": {
              "type": "string",
              "description": "Relevant context for the specialist"
            }
          }
        }
      }
    ]
  }
}
```

## 📋 Best Practices

### 1. Clear Agent Definitions
- Define each "agent's" expertise clearly
- Specify when to use each specialist
- Include handoff protocols

### 2. Context Preservation
- Maintain conversation context across agent switches
- Include relevant history when routing
- Summarize previous agent interactions

### 3. User Experience
- Make routing transparent to users
- Provide clear agent identification
- Offer routing explanations when helpful

### 4. Fallback Strategies
- Handle ambiguous requests gracefully
- Provide agent recommendations
- Allow manual agent selection

## 🎯 Usage Examples

### Example 1: Job Application Workflow
```
User: "I need help with a job application for a Product Manager role at Google"

Coordinator: "I'll coordinate multiple specialists for your Google PM application:

🔍 RESEARCH_AGENT: Analyzing Google's culture and PM role requirements...
📄 RESUME_AGENT: Optimizing your resume for this specific role...  
🎯 COVER_LETTER_AGENT: Crafting a personalized cover letter...
💼 INTERVIEW_AGENT: Preparing PM-specific interview questions...

Let me start with research and then we'll move through each specialist."
```

### Example 2: Career Transition
```
User: "I want to transition from marketing to data science"

Coordinator: "This requires multiple specialists:

📊 DATA_AGENT: Outlining the data science learning path...
📄 RESUME_AGENT: Strategizing your resume transition...
💰 SALARY_AGENT: Researching data science compensation...
🎯 COVER_LETTER_AGENT: Positioning your marketing background as an advantage...

Let's start with the learning roadmap..."
```

## 🔧 Implementation Tips

1. **Start Simple**: Begin with role-based routing, add complexity gradually
2. **Test Thoroughly**: Verify routing logic with various request types
3. **Monitor Performance**: Track which "agents" are used most frequently
4. **Iterate Based on Usage**: Refine routing logic based on user patterns
5. **Maintain Consistency**: Ensure agent personalities remain consistent

This approach gives you the power of multiple specialized models while maintaining the simplicity of a single conversation interface!
