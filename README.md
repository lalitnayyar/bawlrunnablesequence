# Getting Started
Install the dependencies and run the project
```
npm install
npm start
```

Head over to https://vitejs.dev/ to learn more about configuring vite

# Bawl Runnable Sequence

This project demonstrates how to use the `langchain` library to process sentences by adding punctuation and correcting grammar using OpenAI's language model.

## Setup

1. Clone the repository.
2. Install dependencies:
    ```bash
    npm install
    ```
3. Create a `.env` file in the root directory with the following content:
    ```plaintext
    SUPABASE_URL_LC_CHATBOT='your_supabase_url'
    SUPABASE_API_KEY='your_supabase_api_key'
    OPENAI_API_KEY='your_openai_api_key'
    ```

## Vite Configuration

The `vite.config.js` file is configured to load environment variables from the `.env` file:
```javascript
import { defineConfig } from 'vite'
import dotenv from 'dotenv'

dotenv.config()

export default defineConfig({
  define: {
    'process.env': process.env
  }
})
```

## Code Explanation

The main code is in `index.js` and performs the following steps:

1. Import necessary modules from `langchain` and other libraries.
2. Load the OpenAI API key from environment variables.
3. Create a `ChatOpenAI` instance with the API key.
4. Define prompt templates for punctuation and grammar correction.
5. Create a `RunnableSequence` chain that processes the sentence through the prompts and the language model.
6. Invoke the chain with a sample sentence and log the response.

```javascript
import { ChatOpenAI } from 'langchain/chat_models/openai'
import { PromptTemplate } from 'langchain/prompts'
import { StringOutputParser } from 'langchain/schema/output_parser'
import { RunnableSequence } from "langchain/schema/runnable"

const openAIApiKey = process.env.OPENAI_API_KEY
const llm = new ChatOpenAI({ openAIApiKey })

const punctuationTemplate = `Given a sentence, add punctuation where needed. 
    sentence: {sentence}
    sentence with punctuation:  
    `
const punctuationPrompt = PromptTemplate.fromTemplate(punctuationTemplate)

const grammarTemplate = `Given a sentence correct the grammar.
    sentence: {punctuated_sentence}
    sentence with correct grammar: 
    `
const grammarPrompt = PromptTemplate.fromTemplate(grammarTemplate)

const chain = RunnableSequence.from([
    punctuationPrompt,
    llm
])

const response = await chain.invoke({
    sentence: 'i dont liked mondays',
    language: 'french'
})

console.log(response)
```

## Running the Project

To run the project, use the following command:
```bash
npm run dev
```

## About Scrimba

At Scrimba our goal is to create the best possible coding school at the cost of a gym membership! 💜
If we succeed with this, it will give anyone who wants to become a software developer a realistic shot at succeeding, regardless of where they live and the size of their wallets 🎉
The Frontend Developer Career Path aims to teach you everything you need to become a Junior Developer, or you could take a deep-dive with one of our advanced courses 🚀

- [Our courses](https://scrimba.com/allcourses)
- [The Frontend Career Path](https://scrimba.com/learn/frontend)
- [Become a Scrimba Pro member](https://scrimba.com/pricing)

Happy Coding!