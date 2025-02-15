### **1. Data Augmentation**
For Data Augmentation, we are using the jackaduma/SecBERT model in which masked words concept is used. This could be better understood with the help of below example.

✅ Original sentence:
"I received random calls and abusive messages on my WhatsApp."

If we apply masking, we randomly replace a word with [MASK]:

❌ Masked sentence:
"I received random calls and [MASK] messages on my WhatsApp."

The model will then predict possible words to replace [MASK], such as:
🔹 harassing
🔹 spam
🔹 threatening

The model picks one of these words and reconstructs the sentence.


The first step in preprocessing is **data augmentation**. This enhances the dataset by generating variations of existing data, helping improve model generalization. Augmentation methods include:

- Synonym replacement using NLP techniques.
- Random word insertion, deletion, and swapping to create diverse training samples.
- Sentence paraphrasing using AI models to enhance variability.

### **2. Data Translation**

After augmentation, we translate the data using multiple methods:

- **Method 1:** Utilizing Google Sheets formula (`=GoogleTranslate(A2, "hi", "en")`) for quick translation.
- **Method 2:** Using **Ollama**, an advanced NLP-based translation tool for high-quality translations.
- **Method 3:** Leveraging the `deep-translator` library with the **Google Translator API** for real-time Hinglish-to-English conversion.
  - Automatically detects and translates text while handling exceptions.
  - Applied to the `crimeaditionalinfo` column in our dataset.
- **Method 4:** Implementing **MarianMT (Helsinki-NLP/opus-mt-hi-en)**, a transformer-based translation model.
  - Uses tokenization and deep learning to improve translation accuracy.
  - Handles NaN values and refines translations based on context.

This multi-method approach ensures diverse translations and helps maintain linguistic consistency across multiple languages. Google Sheets provides a quick and accessible translation option, Ollama offers nuanced, context-aware translations, Deep Translator handles real-time conversions, and MarianMT applies neural translation techniques.

### **3. Data Cleaning**

Once translation is complete, we apply rigorous data cleaning steps to remove inconsistencies and standardize the text. The cleaning process includes:

- Removing unnecessary special characters and symbols.
- Eliminating URLs and non-alphanumeric characters.
- Correcting spelling mistakes using automated spell-check tools.
- Standardizing abbreviations and terminology.
- Filtering out stopwords and redundant words to retain meaningful information.
- Applying **lemmatization** to reduce words to their base forms.

A custom Python script leveraging **NLTK and regex-based text processing** is used for effective text cleaning.

### **4. Dictionary-Based Enhancement**

To improve the quality of processed data, we incorporate **full forms** of abbreviations and acronyms using:

- **Our custom dictionary** with domain-specific terms related to cybercrime and online fraud.
- **An external dictionary** sourced from "[Provide Reference Source Here]" to supplement our vocabulary expansion.

This step ensures that shorthand notations and abbreviations are replaced with their complete meanings, improving text interpretability for both humans and machine learning models.

### **5. Data Filtering**

To enhance data relevancy and usability, we apply filtering mechanisms:

- **Sentence length filtering:** Removing entries with fewer than three words to eliminate incomplete data.
- **Duplicate removal:** Ensuring each report in the dataset is unique.
- **Irrelevant data elimination:** Filtering out reports that do not align with cybercrime-related incidents.

###
