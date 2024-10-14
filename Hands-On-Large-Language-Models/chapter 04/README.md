## Text Classification Using Transformers

This notebook focuses on **text classification**, using the `transformers` library from Hugging Face. The task involves classifying movie reviews as either positive or negative using a pre-trained model.

### Key Concepts Explored:

1. **Loading the Dataset**:
   - The notebook uses the **Rotten Tomatoes** dataset, loaded from the Hugging Face `datasets` library. This dataset consists of movie reviews labeled as positive or negative.

2. **Task-Specific Model**:
   - The notebook applies a task-specific model: **Twitter RoBERTa (cardiffnlp/twitter-roberta-base-sentiment-latest)**, fine-tuned for sentiment analysis.
   - This model predicts the sentiment (positive or negative) of the text data.

3. **Pipeline for Inference**:
   - A **pipeline** from the `transformers` library is set up to perform inference. The pipeline uses the pre-trained model to make predictions on the dataset.
   - Predictions are made using GPU acceleration (`cuda:0`) for faster processing.

4. **Batch Processing**:
   - The notebook efficiently processes the test dataset using **batch inference** with `tqdm` to track progress and handle large datasets smoothly.

5. **Evaluation**:
   - After predictions are made, the performance of the model is evaluated using the **classification report** from the `sklearn` library.
   - The report provides key metrics such as precision, recall, and F1-score for both positive and negative reviews.
