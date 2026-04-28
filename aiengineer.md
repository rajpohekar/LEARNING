## Tokenization and Mapping Text to Numbers (LLMs)

### 1. Tokenization
Tokenization is the process of breaking input text into smaller units called **tokens** so that a model can process it.

**Example:**
Text:
"I love AI"

Possible tokens:
["I", " love", " AI"]

Tokens are not always full words — they can be:
- Words → "cat"
- Subwords → "un", "happy"
- Characters → "!"

---

### 2. Mapping Tokens to Numbers (Encoding)
After tokenization, each token is converted into a **unique numerical ID** using a vocabulary.

**Example:**
Tokens:
["I", " love", " AI"]

Mapped IDs:
[101, 205, 678]

This mapping is done using a predefined **vocabulary (token → ID dictionary)**.

---

### 3. Why Convert to Numbers?
Neural networks (LLMs) can only process numbers, not text. So:

Text → Tokens → Token IDs → Model Processing

---

### 4. Full Flow
"I love AI"
   ↓
Tokenization
   ↓
["I", " love", " AI"]
   ↓
Mapping (Encoding)
   ↓
[101, 205, 678]
   ↓
Input to LLM

---

### 5. Important Note
- Same word can have different tokens depending on context.
- Different models use different tokenization methods (BPE, WordPiece, SentencePiece).
- Token count affects:
  - Cost (API usage)
  - Input/output limits

---

### 6. Simple Analogy
Think of tokenization like splitting a sentence into Lego blocks,  
and mapping is assigning a number to each block so the machine can understand it.
