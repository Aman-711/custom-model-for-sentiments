 Training Individual Models
ViT (Vision Transformer) Model for Images:
A Vision Transformer was trained to classify images into two categories: informative and non-informative.
The model was fine-tuned on image data with its classification layer trained for this specific task.
BERT Model for Text:
A BERT-based model was trained to classify text (e.g., tweets) into the same categories (informative and non-informative).
The text data was tokenized, and BERT's classification layer was fine-tuned during training.

Uploading the Pretrained Models
After training, both the ViT and BERT models were saved and then loaded back into a new environment to create a combined multimodal model.

Modifications to the Models
Classification Layer Removal:

The classification layers (final layers) of both models were removed because they were task-specific and not needed for feature extraction.
This allowed the models to act as feature extractors that output high-dimensional embeddings (representations) of their respective inputs (images or text).
Freezing Hyperparameters:

All the parameters (weights) of the ViT and BERT models were frozen.
This ensures that during training of the combined model, the pretrained weights of these models remain unchanged and only the newly added layers are trained.

Connecting the Models with a Fully Connected Layer
A Fully Connected (FC) Layer was added to combine the features extracted by the ViT and BERT models.
The embeddings (outputs) from both models were concatenated to create a single combined feature vector.
This combined vector was passed through a fully connected layer with:
A hidden layer (to learn meaningful relationships between text and image features).
An output layer with 2 neurons for binary classification (Positive or Negative).

Multimodal Training
The combined model was trained on multimodal data (text and images) for binary classification:
Text Data: Passed through the BERT feature extractor.
Image Data: Passed through the ViT feature extractor.
Combined Features: The extracted features from both modalities were fed into the fully connected layer for final classification.
