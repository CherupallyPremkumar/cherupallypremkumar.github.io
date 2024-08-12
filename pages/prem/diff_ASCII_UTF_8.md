---
title: ASCII vs UTF-8
keywords: homepage
tags: [autonomy introduction modulith chenile]
sidebar: chenile_sidebar
permalink: /ascii-vs-utf8.html
summary: We explain the Autonomy Pyramid. Then we talk about Chenile's recommendation 
---

### 1\. Single-Byte Character Sets (like ASCII)

*   **ASCII**: This is a basic character set that represents English letters, digits, and some symbols. Each character in ASCII is stored using 1 byte (8 bits).
    
    *   For example, the word "Hello" in ASCII would take up 5 bytes (1 byte per character).
        

### 2\. Multibyte Character Sets (like UTF-8)

*   Here's how it works:
    
    *   **1 byte**: For characters that are part of the standard ASCII set (like A-Z, a-z, 0-9, and basic punctuation).
        
    *   **2 bytes**: For characters in many Western European languages, such as é, ä, etc.
        
    *   **3 bytes**: For characters in other languages, such as Greek, Cyrillic, or Hebrew.
        
    *   **4 bytes**: For more complex characters, like emojis or some characters in Asian languages (e.g., Chinese, Japanese, Korean).
        

### Example with ASCII and UTF-8:

Let’s compare how the word "Hello" and a non-English word would be stored:

*   **"Hello" in ASCII**:
    
    *   "H", "e", "l", "l", "o" → Each character is 1 byte.
        
    *   Total: 5 characters × 1 byte = 5 bytes.
        
*   **"Hello" in UTF-8**:
    
    *   "H", "e", "l", "l", "o" → Each character is still 1 byte.
        
    *   Total: 5 characters × 1 byte = 5 bytes.
        

But consider a non-English word like "Olá" (Portuguese for "Hello"):

*   **"Olá" in UTF-8**:
    
    *   "O", "l", "a" → Each character might be 1 byte.
        
    *   "á" → This character á is stored in 2 bytes because it’s not part of the basic ASCII set.
        
    *   Total: 2 characters × 1 byte + 1 character × 2 bytes = 4 bytes.
        

For an even more complex example:

*   **"你好" (Chinese for "Hello") in UTF-8**:
    
    *   Each Chinese character might require 3 bytes.
        
    *   Total: 2 characters × 3 bytes = 6 bytes.
        

### Key Takeaways

*   **Single-Byte (ASCII)**: Each character is stored using 1 byte. This is simple and consistent but limited to basic English characters and symbols.
    
*   **Multibyte (UTF-8)**: Storage varies. Basic English characters still take 1 byte, but characters from other languages or symbols can take 2, 3, or even 4 bytes.
    

### Why This Matters

When designing a database, it’s important to consider the character set your text will use. If your application will store only English text, ASCII might be sufficient. But if you need to support multiple languages, UTF-8 is more flexible, though it may require more storage per character.