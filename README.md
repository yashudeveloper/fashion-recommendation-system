# Fashion Recommendation System

## Project Overview
The **Fashion Recommendation System** is an AI-driven tool that helps consumers discover stylish outfit suggestions based on an input image. By analyzing the provided image, the system generates **text-based outfit recommendations** and retrieves visually similar clothing items from a database. 

### Key Features:
- **AI-Powered Outfit Suggestions**: Provides personalized clothing recommendations.
- **Visual Search**: Retrieves similar fashion items from a dataset.
- **Seamless Image Input**: Users can provide an image URL for analysis.
- **Text & Visual Suggestions**: Generates textual outfit ideas and finds matching visuals.
- **Google Colab Compatibility**: Easy to run without local setup.

## Dependencies
To ensure compatibility, the following dependencies are required:
```bash
pip install bitsandbytes unsloth transformers datasets huggingface_hub torch PIL pandas requests
```
- **Python Version**: 3.11

## Setup Instructions
### Step 1: Open Google Colab
Since this project runs best in **Google Colab**, open Colab and create a new notebook.

### Step 2: Install Dependencies
Run the following command in a code cell:
```bash
!pip install bitsandbytes unsloth transformers datasets huggingface_hub torch PIL pandas requests
```

### Step 3: Load the Pretrained Model
No separate model download is needed. Ensure that you **insert your API token** at necessary places.
```python
from unsloth import FastVisionModel
model, tokenizer = FastVisionModel.from_pretrained("unsloth/Llama-3.2-11B-Vision-Instruct", load_in_4bit=True, token="YOUR_TOKEN_HERE")
```

### Step 4: Input Image for Recommendation
Provide an image URL as follows:
```python
from PIL import Image
import requests
from io import BytesIO

image_url = "IMAGE_URL_HERE"
response = requests.get(image_url)
image = Image.open(BytesIO(response.content)).convert("RGB")
```

### Step 5: Generate Recommendations
Run the model to get outfit suggestions:
```python
instruction = "Suggest complementary outfit items for this image."
output = model.generate_suggestions(image, instruction)
print(output)
```

### Step 6: Retrieve Matching Visuals
The system then searches the fashion database for similar styles.
```python
matching_items = search_fashion_database(output)
display_results(matching_items)
```

## Future Plans
To enhance the project further, we plan to:
1. **AI-Powered Outfit Generator** – Use generative AI to visualize entire outfits.
2. **Personalized Recommendations** – Implement user profiles for customized styling.
3. **Augmented Reality (AR) Try-On** – Allow users to see how outfits look in real-time.
4. **E-Commerce Integration** – Link suggestions directly to online stores for purchase.
5. **Mobile App Expansion** – Convert the system into an accessible cross-platform app.

## Team Members
- **Yash Bhardwaj** – Full Stack, Web Development
- **Sarthak Sahu** – Full Stack, ML Implementation
- **Aditya Goel** – Full Stack, Web Development
- **Manjeet Sharma** – Full Stack, Data Collection

## License
This project is released under the **MIT License**.

## Contribution Guidelines
We welcome contributions! Please follow these steps:
1. Fork the repository.
2. Create a new branch (`feature-branch`).
3. Commit your changes.
4. Open a pull request with a detailed description.

---
### Enjoy discovering new fashion styles effortlessly! 👗🛍️

