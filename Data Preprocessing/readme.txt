For Data Augmentation, we are using the jackaduma/SecBERT model in which masked words context is used:

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
