# Cover Letter Genie - Open WebUI Model Configurations

This repository contains various JSON configuration examples for importing custom models into Open WebUI. These examples range from minimal configurations to complex, feature-rich setups.

## How to Import

1. Go to your Open WebUI interface
2. Navigate to **Settings** → **Models**
3. Click **"Import Model"** or the **"+"** button
4. Upload any of the JSON files below
5. The model will appear in your model list

## Configuration Examples

### 1. Minimal Configuration
*Perfect for quick setups with basic functionality*

```json
{
  "id": "simple-assistant",
  "name": "Simple Assistant",
  "base_model_id": "gpt-3.5-turbo",
  "params": {
    "system": "You are a helpful assistant."
  }
}
```

### 2. Standard Configuration
*Balanced setup with common parameters and metadata*

```json
{
  "id": "cover-letter-helper",
  "name": "Cover Letter Helper",
  "meta": {
    "description": "Assists with writing professional cover letters",
    "author": "tommy-2-hats",
    "tags": ["writing", "job-search"],
    "version": "1.0.0"
  },
  "base_model_id": "gpt-4",
  "params": {
    "system": "You are a professional writing assistant specializing in cover letters. Help users create compelling, personalized cover letters that highlight their strengths.",
    "temperature": 0.7,
    "max_tokens": 800,
    "top_p": 0.9
  }
}
```

### 3. Advanced Configuration
*Comprehensive setup with fine-tuned parameters and detailed metadata*

```json
{
  "id": "cover-letter-genie",
  "name": "Cover Letter Genie",
  "meta": {
    "description": "A specialized model for generating personalized cover letters",
    "author": "tommy-2-hats",
    "tags": ["cover-letter", "job-application", "writing-assistant"],
    "version": "1.0.0",
    "license": "MIT",
    "repository": "https://github.com/tommy-2-hats/cover-letter-genie"
  },
  "base_model_id": "gpt-4-turbo",
  "params": {
    "system": "You are Cover Letter Genie, an expert at crafting personalized, compelling cover letters. You help job seekers create tailored cover letters that highlight their relevant skills and experience for specific positions. Always ask for the job description, company information, and the user's background before generating a cover letter.",
    "temperature": 0.7,
    "top_p": 0.9,
    "max_tokens": 1000,
    "frequency_penalty": 0.1,
    "presence_penalty": 0.1,
    "stop": ["\n\n---", "END_LETTER"]
  },
  "info": {
    "base": {
      "name": "GPT-4 Turbo",
      "size": "Unknown"
    },
    "capabilities": ["text-generation", "conversation"],
    "pricing": {
      "input": 0.01,
      "output": 0.03
    }
  }
}
```

### 4. Complex Multi-Purpose Configuration
*Enterprise-level setup with multiple personas and advanced features*

```json
{
  "id": "career-advisor-pro",
  "name": "Career Advisor Pro",
  "meta": {
    "description": "Comprehensive career guidance including cover letters, resume reviews, interview prep, and salary negotiations",
    "author": "tommy-2-hats",
    "tags": ["career", "job-search", "interview", "resume", "cover-letter", "salary", "professional-development"],
    "version": "2.1.0",
    "license": "MIT",
    "repository": "https://github.com/tommy-2-hats/cover-letter-genie",
    "documentation": "https://docs.example.com/career-advisor-pro",
    "support": "support@example.com",
    "category": "Professional Services"
  },
  "base_model_id": "gpt-4-turbo",
  "params": {
    "system": "You are Career Advisor Pro, a comprehensive career guidance expert with multiple specializations:\n\n**COVER LETTERS**: Craft personalized, compelling cover letters that showcase relevant experience and align with job requirements.\n\n**RESUME REVIEW**: Analyze and improve resumes for ATS optimization, formatting, and content enhancement.\n\n**INTERVIEW PREP**: Provide mock interview questions, answer frameworks (STAR method), and industry-specific guidance.\n\n**SALARY NEGOTIATION**: Offer data-driven salary insights and negotiation strategies.\n\n**CAREER PLANNING**: Help with career transitions, skill development, and professional growth strategies.\n\nAlways:\n- Ask clarifying questions to understand the user's specific situation\n- Provide actionable, personalized advice\n- Include relevant industry insights and current market trends\n- Offer follow-up suggestions for continued improvement\n\nStart each conversation by asking what specific career area the user needs help with.",
    "temperature": 0.8,
    "top_p": 0.95,
    "max_tokens": 1500,
    "frequency_penalty": 0.2,
    "presence_penalty": 0.15,
    "stop": ["\n---END---", "CONVERSATION_COMPLETE"],
    "seed": 42
  },
  "info": {
    "base": {
      "name": "GPT-4 Turbo",
      "size": "175B parameters",
      "provider": "OpenAI"
    },
    "capabilities": [
      "text-generation",
      "conversation",
      "analysis",
      "professional-writing",
      "career-guidance"
    ],
    "pricing": {
      "input": 0.01,
      "output": 0.03,
      "currency": "USD",
      "per": "1K tokens"
    },
    "performance": {
      "avg_response_time": "2-4 seconds",
      "accuracy_rating": "95%",
      "user_satisfaction": "4.8/5"
    }
  },
  "config": {
    "streaming": true,
    "context_length": 128000,
    "supports_functions": true,
    "supports_vision": false,
    "rate_limit": {
      "requests_per_minute": 60,
      "tokens_per_minute": 40000
    }
  }
}
```

## Configuration Fields Reference

### Required Fields
- **`id`**: Unique identifier for your model
- **`name`**: Display name in Open WebUI
- **`base_model_id`**: The underlying model to use

### Optional Fields

#### Meta Information
- **`description`**: Brief description of the model's purpose
- **`author`**: Creator of the configuration
- **`tags`**: Array of relevant keywords
- **`version`**: Version number
- **`license`**: License type
- **`repository`**: GitHub or source repository URL

#### Parameters (`params`)
- **`system`**: System prompt defining model behavior
- **`temperature`**: Randomness control (0.0-2.0)
- **`top_p`**: Nucleus sampling parameter (0.0-1.0)
- **`max_tokens`**: Maximum response length
- **`frequency_penalty`**: Reduces word repetition (-2.0 to 2.0)
- **`presence_penalty`**: Encourages topic diversity (-2.0 to 2.0)
- **`stop`**: Array of stop sequences
- **`seed`**: For reproducible outputs

#### Info Section
- **`base`**: Information about the base model
- **`capabilities`**: Array of model capabilities
- **`pricing`**: Cost information
- **`performance`**: Performance metrics

#### Config Section (Advanced)
- **`streaming`**: Enable streaming responses
- **`context_length`**: Maximum context window
- **`supports_functions`**: Function calling support
- **`rate_limit`**: API rate limiting information

## Tips for Customization

1. **Start Simple**: Begin with a minimal configuration and add complexity as needed
2. **Test Parameters**: Experiment with temperature and other parameters to find optimal settings
3. **Clear System Prompts**: Write specific, clear instructions for your model's behavior
4. **Version Control**: Use semantic versioning for your configurations
5. **Documentation**: Include comprehensive metadata for team collaboration

## Common Base Models

- `gpt-3.5-turbo` - Fast and cost-effective
- `gpt-4` - High quality reasoning
- `gpt-4-turbo` - Latest GPT-4 with larger context
- `claude-3-sonnet` - Anthropic's balanced model
- `llama2` - Open source alternative
- `mistral-7b` - Efficient open source model

Choose the base model that best fits your use case, budget, and performance requirements.