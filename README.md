# Detailed Project Report: ShopAssist AI

## 1. Project Title
**ShopAssist AI: An Intelligent Conversational Assistant for Product Recommendations**

## 2. Objectives
The objective of the ShopAssist AI project is to design and develop an AI-powered conversational assistant that:
- Engages users through natural language to understand their product requirements (e.g., laptops).
- Asks targeted follow-up questions to clarify preferences such as budget, screen size, RAM, and usage.
- Matches the user-defined requirements with a structured product dataset.
- Returns personalized and relevant product recommendations.
- Demonstrates the integration of Large Language Models (LLMs) with real-world tabular data.

## 3. System Design

### 3.1 Components
- **LLM Interaction Layer**: Utilizes OpenAI’s GPT API to understand, interact, and reason with the user.
- **Prompt Engineering**: Incorporates few-shot learning and chain-of-thought prompting to guide the assistant’s dialogue.
- **Data Handler**: Loads and processes the laptop dataset (`laptop_data.csv`) using pandas.
- **Matching Engine**: Filters products from the dataset based on inferred preferences from the conversation.

### 3.2 Flow
1. Assistant greets and asks initial preferences.
2. Captures responses iteratively using GPT's memory of the conversation.
3. Once the user’s needs are clear, the assistant applies filters on the dataset.
4. The assistant suggests the top matching products.

## 4. Implementation

### 4.1 Technology Stack
- **Language**: Python
- **Libraries**: OpenAI, pandas, numpy, tenacity
- **Platform**: Google Colab + Google Drive
- **Dataset**: A CSV file with laptop specifications (brand, processor, RAM, price, etc.)

### 4.2 Key Functions
- `initialize_conversation()`: Sets up the system and assistant prompts for a contextual and guided chat.
- `get_chat_completions()`: Interfaces with OpenAI’s API using retry logic to handle transient errors.
- `iterate_response()`: Organizes and displays the interaction step-by-step.
- `read_csv_from_drive()`: Loads the product data from Google Drive.
- Chat loop: Maintains conversation until the assistant gathers complete product criteria.

## 5. Challenges Faced

### 5.1 Prompt Engineering
- Designing effective prompts that guide the assistant to ask relevant questions without overwhelming the user was challenging.
- Iterative refinement was needed to make the assistant sound helpful and human-like.

### 5.2 Handling Ambiguity
- Users may provide vague or partial inputs. The assistant needed to gracefully handle such ambiguity and prompt for clarification.

### 5.3 API Rate Limits
- OpenAI API usage was rate-limited. To mitigate this, the project used the `tenacity` library to implement retries.

### 5.4 Data Matching
- Translating free-text preferences into structured filters required careful design.
- Mapping qualitative terms (e.g., “light gaming”) to quantitative attributes (e.g., GPU presence) involved assumptions and tuning.

## 6. Lessons Learned
- **LLMs excel with the right prompts**: The behavior of the AI assistant is highly sensitive to the design of the system prompt and few-shot examples.
- **User experience matters**: Progressive, friendly questioning helps gather accurate product needs and improves satisfaction.
- **Retry logic is essential**: Production-ready API integrations must be resilient to transient errors.
- **Integration is powerful**: Bridging the gap between unstructured human input and structured datasets is a key value proposition of conversational AI.

## 7. Conclusion
ShopAssist AI effectively demonstrates how conversational AI, when integrated with structured product data, can enhance decision-making and user experience in e-commerce or digital assistants. The assistant is capable of real-time conversation, progressive need discovery, and actionable product recommendations. This project lays the foundation for scaling such assistants to other domains like smartphones, appliances, or even insurance plans.
