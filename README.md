# **Assignment 2: Advanced Problem Solving with Python**

**Contributors:**

- [**Ibtesam Ahmed Dar | S376904**](mailto:s376904@students.cdu.edu.au)
- [**Shahrukh | S373435**](mailto:s373435@students.cdu.edu.au)
- [**Asim Nawaz | S375640**](mailto:s375640@students.cdu.edu.au)

---

## **Table of Contents**

1. [Introduction](#introduction)
2. [Question 1: Named Entity Recognition (NER) and Model Comparison](#question-1-named-entity-recognition-ner-and-model-comparison)
   - [Problem Statement](#question-1-problem-statement)
   - [Approach and Methodology](#question-1-approach-and-methodology)
   - [Challenges and Solutions](#question-1-challenges-and-solutions)
3. [Question 2: Image Mutation and Pixel Manipulation](#question-2-image-mutation-and-pixel-manipulation)
   - [Problem Statement](#question-2-problem-statement)
   - [Approach and Methodology](#question-2-approach-and-methodology)
   - [Challenges and Solutions](#question-2-challenges-and-solutions)
   - [Output Image](#question-2-output-image)
4. [Question 3: Decryption and Correction of Error-Prone Code](#question-3-decryption-and-correction-of-error-prone-code)
   - [Problem Statement](#question-3-problem-statement)
   - [Approach and Methodology](#question-3-approach-and-methodology)
   - [Challenges and Solutions](#question-3-challenges-and-solutions)
5. [Summary](#summary)

---

## **Introduction**

This repository contains solutions to Assignment 2 for our Advanced Programming course. It includes three different problems that test our knowledge of Python in various aspects:

- **Image Processing and Image Manipulation**
- **Natural Language Processing (NLP) & Machine Learning**
- **Code Decryption and Debugging**

Our team—Ibtesam Ahmed Dar, Shahrukh, and Asim Nawaz—worked collaboratively to solve these challenges. Together, we utilized our unique strengths, conducted thorough research, and extensively tested our solutions to ensure they meet high standards.

---

## **Question 1: Named Entity Recognition (NER) and Model Comparison**

### **Problem Statement**

The objective was to extract entities related to diseases and drugs from a given text file using two different NER models:

1. **SciSpacy Models**:
   - `en_core_sci_sm`
   - `en_ner_bc5cdr_md`

2. **BioBERT Model**:
   - A pre-trained transformer model fine-tuned for biomedical NER tasks.

We were to compare the models based on:

- Total entities detected.
- Most common entities extracted.
- Differences in model outputs and performance.

### **Approach and Methodology**

1. **Data Preparation**:

   - Loaded the text data from the provided file.
   - Preprocessed the text to ensure compatibility with both models (e.g., handling special characters, tokenization).

2. **NER with SciSpacy**:

   - Installed and loaded the SciSpacy models.
   - Processed the text to extract entities labeled as diseases and drugs.
   - Collected and stored entities for analysis.

3. **NER with BioBERT**:

   - Utilized the Hugging Face `transformers` library to load the BioBERT model.
   - Tokenized the text using the appropriate tokenizer for BioBERT.
   - Ran the model to extract entities, applying the necessary decoding to interpret model outputs.
   - Gathered the entities for comparison.

4. **Analysis and Comparison**:

   - Calculated the total number of entities detected by each model.
   - Identified the most common entities and their frequencies.
   - Compared the entities extracted by both models to find overlaps and discrepancies.
   - Analyzed precision, recall, and F1 scores where possible to evaluate model performance.

### **Challenges and Solutions**

- **Model Compatibility and Dependencies**:

  - **Challenge**: Installing and setting up both SciSpacy and BioBERT models required resolving dependency conflicts.
  - **Solution**: Created isolated virtual environments for each model and carefully managed package versions.

- **Differences in Model Outputs**:

  - **Challenge**: The two models output entities in different formats and with varying levels of granularity.
  - **Solution**: Developed a standard format for entities and wrote parsing functions to normalize outputs for fair comparison.

- **Computational Resources**:

  - **Challenge**: BioBERT is resource-intensive and required significant computational power.
  - **Solution**: Used Google Colab with GPU acceleration to run BioBERT efficiently.

- **Evaluating Model Performance**:

  - **Challenge**: Difficulty in quantitatively comparing models without a labeled dataset for calculating metrics like precision and recall.
  - **Solution**: Focused on qualitative analysis and frequency counts, and discussed potential impacts on model selection in real-world applications.

---

## **Question 2: Image Mutation and Pixel Manipulation**

### **Problem Statement**

Our task was to transform an image by injecting a random number into one of the channels—red, green, or blue (RGB)—of every pixel. The random number was to depend on the parity of the system time. Specifically:

- **Random Number Generation**: Generate a time-based random number. If the number is even, add 10 to it to satisfy task conditions.
- **Image Manipulation**: Load an image, convert it to a NumPy array, and apply the generated number to the RGB channels of all pixels.
- **Output Requirements**:
  - Save the mutated image under a new filename.
  - Compute and output the sum of all red pixel values in the modified image.

### **Approach and Methodology**

1. **Image Loading and Conversion**:

   - Used **PIL (Python Imaging Library)** to load the original image.
   - Converted the image to a NumPy array using `numpy.asarray()` for efficient pixel-level manipulation.

2. **Random Number Generation**:

   - Generated a random number based on the current system time using the `time` and `random` modules.
   - Checked the parity of the number:
     - If **even**, added 10 to ensure it met the task's conditions.
     - If **odd**, used the number as-is.

3. **Pixel Manipulation**:

   - Added the generated number to the RGB channels of every pixel using NumPy's array operations.
   - Ensured pixel values remained within the valid range (0-255) using `numpy.clip()` to prevent overflow or underflow.

4. **Saving and Outputting Results**:

   - Saved the mutated image with a new filename to preserve the original image.
   - Calculated the sum of all red pixel values using NumPy's slicing and `sum()` functions.
   - Displayed the mutated image and printed the computed sum for verification.

### **Challenges and Solutions**

- **Pixel Value Overflow**:

  - **Challenge**: Adding a number to pixel values risked exceeding the maximum allowable value (255), causing color distortions.
  - **Solution**: Implemented `numpy.clip()` to constrain pixel values within the 0-255 range.

- **Efficiency in Pixel Manipulation**:

  - **Challenge**: Looping through each pixel individually would be inefficient for large images.
  - **Solution**: Leveraged NumPy's ability to perform element-wise operations on arrays, allowing us to manipulate all pixels simultaneously.

- **Random Number Consistency**:

  - **Challenge**: Ensuring the random number was consistent throughout the manipulation process.
  - **Solution**: Generated the random number once and stored it in a variable used across all computations.

### **Output Image**

![Image could not load](Files_s375640_s373435_s376904_Question02_Chapter01_ColabNotebook/chapter1out.png "chapter1out.png")

---

## **Question 3: Decryption and Correction of Error-Prone Code**

### **Problem Statement**

We were provided with an encrypted Python script that, upon decryption, revealed code containing multiple syntax and logical errors. Our tasks were:

1. **Decrypt the Code**: Determine the encryption method and retrieve the original code.
2. **Fix the Errors**: Identify and correct all syntax and logical errors in the code.
3. **Explain the Corrections**: Add comments explaining each fix and the reason behind it.

### **Approach and Methodology**

1. **Decryption Process**:

   - **Encryption Analysis**:
     - Noted that the encrypted code seemed to use a substitution cipher resembling ROT13.
   - **Decryption Implementation**:
     - Wrote a decryption function that shifted alphabetic characters by 13 places.
     - Applied the function to the encrypted code to obtain the original script.

2. **Error Identification and Correction**:

   - **Syntax Errors**:
     - Incorrect keywords (e.g., `qrs` instead of `def`).
     - Misuse of colons, commas, and indentation issues.
   - **Logical Errors**:
     - Improper use of global variables.
     - Faulty loop constructs and conditional statements.
     - Incorrect function calls and parameter usage.
   - **Corrections**:
     - Replaced incorrect keywords with valid Python syntax.
     - Fixed variable names for clarity.
     - Adjusted function definitions and calls.
     - Corrected loop and conditional logic.
     - Added necessary global statements and proper indentation.

3. **Documentation and Explanation**:

   - Added comprehensive comments explaining each correction.
   - Provided reasoning for changes to improve code readability and functionality.

### **Challenges and Solutions**

- **Understanding Obfuscated Code**:

  - **Challenge**: The decrypted code had confusing variable names and structures, making it hard to interpret.
  - **Solution**: Renamed variables and functions to meaningful names to better understand their purposes before fixing errors.

- **Ensuring Functional Integrity**:

  - **Challenge**: Fixing syntax errors was straightforward, but ensuring the corrected code behaved as intended required careful analysis.
  - **Solution**: Wrote test cases and printed intermediate outputs to verify each part of the code worked correctly after fixes.

- **Commenting Without Overloading**:

  - **Challenge**: Needed to provide explanations without cluttering the code.
  - **Solution**: Kept comments concise and relevant, focusing on the purpose of each correction.

---

## **Summary**

- **Image Processing**: We deepened our understanding of pixel-level manipulations and the importance of efficient computation.
- **Natural Language Processing**: Gained hands-on experience with advanced NLP models and the complexities involved in model comparison.
- **Code Debugging and Decryption**: Enhanced our problem-solving abilities in decrypting and debugging code, emphasizing attention to detail.

