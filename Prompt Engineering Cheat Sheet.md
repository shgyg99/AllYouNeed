# ✨ **Prompt Engineering Cheat Sheet**

---

## 🎯 **What is Prompt Engineering?**
Prompt engineering is the art and science of crafting effective instructions or inputs to guide AI models, such as GPT or Codex, to generate desired outputs. This cheat sheet outlines best practices, patterns, and tips for creating effective prompts for AI models.

---

## 🔑 **Key Components of a Prompt**

1. **Instruction:**
   - Clearly state what you want the model to do.
   ```
   Summarize the following article in three sentences:
   ```

2. **Context:**
   - Provide background information or examples to guide the model.
   ```
   Context: This is a formal email about a business proposal.
   ```

3. **Input Data:**
   - Supply any specific data or examples.
   ```
   Input: "The quick brown fox jumps over the lazy dog."
   ```

4. **Output Format:**
   - Specify the desired structure or format of the output.
   ```
   Format the output as a numbered list.
   ```

---

## 🛠 **Prompt Design Techniques**

### 1️⃣ **Clarity is Key**
- Use simple, clear, and direct language.
- Avoid ambiguity.
- Example:
  ```
  Write a Python function to calculate the factorial of a number.
  ```

### 2️⃣ **Add Examples**
- Provide positive and negative examples to set expectations.
- Example:
  ```
  Convert these sentences to passive voice:
  Active: "The dog chased the cat."
  Passive: "The cat was chased by the dog."
  Active: "She wrote a book."
  Passive:
  ```

### 3️⃣ **Iterative Refinement**
- Refine prompts through trial and error to improve results.
- Example:
  ```
  Draft a professional email for a job application.
  [Add details like job title, company, and tone.]
  ```

### 4️⃣ **Specify Constraints**
- Use constraints to control length, style, or detail.
- Example:
  ```
  Summarize this paragraph in less than 50 words.
  ```

### 5️⃣ **Break Down Complex Tasks**
- Split multi-step tasks into simpler sub-prompts.
- Example:
  ```
  1. Extract the main idea of this text.
  2. Rewrite it as a headline.
  ```

---

## 🌟 **Best Practices**

### 🔍 **General Tips**
1. **Be Specific:**
   - Vague: "Tell me about cats."
   - Specific: "List five unique traits of Siamese cats."

2. **Guide the Tone:**
   - Casual: "Write a fun fact about dolphins."
   - Formal: "Compose an informative article on dolphin intelligence."

3. **Use Explicit Instructions:**
   - Poor: "Explain climate change."
   - Better: "Write a 300-word essay on climate change for middle school students."

4. **Leverage Model Strengths:**
   - Use AI models for summarization, translation, code generation, creative writing, etc.

---

## 📋 **Common Patterns**

### 1️⃣ **Q&A**
- Input:
  ```
  Question: What is the capital of France?
  Answer:
  ```

### 2️⃣ **Text Transformation**
- Input:
  ```
  Transform this text into bullet points:
  "Machine learning is a subset of AI. It allows computers to learn from data."
  ```

### 3️⃣ **Summarization**
- Input:
  ```
  Summarize the following article in two sentences:
  "Artificial Intelligence is rapidly evolving and impacting various industries..."
  ```

### 4️⃣ **Creative Writing**
- Input:
  ```
  Write a short story about a robot exploring Mars.
  ```

### 5️⃣ **Code Generation**
- Input:
  ```
  Write a function in Python to reverse a string.
  ```

### 6️⃣ **Data Extraction**
- Input:
  ```
  Extract the names of all countries mentioned in this text:
  "France, Germany, and Italy are members of the EU."
  ```

---

## 🚩 **Avoid Common Pitfalls**

1. **Overloading the Prompt:**
   - Avoid: "Translate this text, summarize it, and provide a critique."
   - Better: Separate tasks into individual prompts.

2. **Assuming Prior Knowledge:**
   - Avoid: "Explain how this works."
   - Better: "Explain how quantum computing works to a beginner."

3. **Ambiguity:**
   - Avoid: "Describe this topic."
   - Better: "Describe the process of photosynthesis for a 5th-grade student."

---

## 🔧 **Testing and Iteration**

1. **Experiment with Variations:**
   - Test different phrasings to find the most effective prompt.
2. **Review Outputs:**
   - Analyze results for clarity, accuracy, and completeness.
3. **Incorporate Feedback:**
   - Refine prompts based on real-world usage and outcomes.

---

## 🌐 **Resources for Further Learning**
- [OpenAI API Documentation](https://platform.openai.com/docs/)
- [Prompt Engineering Guide](https://www.promptingguide.ai/)
- [AI Writing Best Practices](https://www.aiwritingresources.com/)

---

🌟 **Master the art of prompting to unlock the true potential of AI!** 🚀

