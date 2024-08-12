The space allocated for a VARCHAR (variable character) field in a database depends on two factors:

1.  **Declared Maximum Length**: This is the maximum number of characters you specify when defining the VARCHAR field, e.g., VARCHAR(255).
    
2.  **Actual Data Stored**: The actual number of characters stored in the field for each row.
    

### Space Allocation

*   **Storage Per Character**: Each character in a VARCHAR field typically requires 1 byte of storage for a single-byte character set (like ASCII). For multibyte character sets (like UTF-8), each character may require 1 to 4 bytes, depending on the specific character.
    
*   **Length Information**: In addition to the storage for the actual characters, VARCHAR fields require additional storage for the length information. This is typically 1 or 2 bytes:
    
    *   1 byte if the maximum length is 255 characters or less.
        
    *   2 bytes if the maximum length exceeds 255 characters.
        

### Example

If you define a VARCHAR(255) column and store the word "Hello" in it, the space allocated would be:

*   **Data**: "Hello" is 5 characters, so it takes 5 bytes (assuming a single-byte character set like ASCII).
    
*   **Length Information**: Since the maximum length is 255, the length field would require 1 byte.
    

So, the total space allocated for this entry is:

*   **5 bytes (data) + 1 byte (length information) = 6 bytes**
    

### Key Points:

*   **Unused Space**: Unlike CHAR fields, which always allocate the full defined length (padded with spaces if necessary), VARCHAR fields only allocate space for the actual data stored plus the length information. This makes VARCHAR more space-efficient for variable-length data.
    
*   **Maximum Length Consideration**: The maximum length you specify (VARCHAR(N)) determines how many characters the field can store. However, the actual storage used depends on the data length.
    
*   **Performance Consideration**: While VARCHAR saves space compared to CHAR, it may lead to more fragmentation and slightly slower performance for certain operations due to the variable length.
    

In summary, the space allocated for a VARCHAR field is the actual number of characters stored (in bytes) plus 1 or 2 bytes for length information, depending on the maximum length defined.