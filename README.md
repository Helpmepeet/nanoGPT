# nanoGPT


# Training Report: nanoGPT

This report documents the iterative improvement of a character-level GPT model trained on the Tiny Shakespeare dataset. It tracks the transition from a basic Bigram-like performance to a more coherent Transformer model.

## Version 1: Constant Learning Rate (Baseline)

* **Parameters:** Learning Rate = 0.05, Epochs = 1000
* **Optimizer:** SGD (Standard Gradient Descent)
* **Observation:** The model struggles with basic English structure. It outputs mostly gibberish with frequent non-existent words.

<img width="669" height="440" alt="image" src="https://github.com/user-attachments/assets/cd4c76df-5a20-4e1b-a86c-a6d17e81a480" />




**Generated Output:**

<img width="794" height="280" alt="image" src="https://github.com/user-attachments/assets/f62c4ee9-0684-414f-93a3-4af21f9e2cf1" />


Serof?
BUKE thinde RW"

---

## Version 2: Switching to AdamW

* **Parameters:** Learning Rate = 3e-4, Epochs = 1000
* **Optimizer:** AdamW
* **Observation:** Significant improvement. By using the AdamW optimizer (which adapts the learning rate for each parameter), the model begins to recognize character names (KING RICHARD II) and uses actual English words, though the sentences lack logical cohesion.

<img width="665" height="438" alt="image" src="https://github.com/user-attachments/assets/f224e596-e613-49ae-9fd3-9f4bf6d7d89a" />




**Generated Output:**

<img width="796" height="332" alt="image" src="https://github.com/user-attachments/assets/f38159a5-1cbf-4a88-85a6-741fd69f7d33" />


---

## Version 3: Introducing Dropout

* **Parameters:** Epochs = 1000, Optimizer = AdamW, Dropout = 0.1
* **Observation:** Dropout was added to prevent the model from memorizing the training data (overfitting). While the 1000-epoch output is similar to Version 2, the model is now better prepared for longer training sessions without becoming "rigid."

<img width="666" height="437" alt="image" src="https://github.com/user-attachments/assets/5381028f-6b5c-4bae-9a8a-a302e2c5f7d6" />




**Generated Output:**

<img width="798" height="370" alt="image" src="https://github.com/user-attachments/assets/5f48736d-4a07-4d4d-b28c-03907ba2f91b" />


---

## Final Version: Optimized Hyperparameters & Extended Training

* **Parameters:** Epochs = 5000, Optimized Head Size/Embedding, Dropout = 0.2
* **Observation:** This is the most "literary" version. After 5000 epochs, the model understands dialogue formatting (Character Name followed by text), basic punctuation, and simple sentence structures. It mimics the "rhythm" of Shakespeare effectively.

<img width="677" height="437" alt="image" src="https://github.com/user-attachments/assets/fa5e0db1-cfeb-467a-85af-5d11782df48d" />



**Generated Output:**

<img width="790" height="387" alt="image" src="https://github.com/user-attachments/assets/90c75051-e05c-4166-a0e9-adb521d8cf67" />


---

## Summary of Findings

| Version | Key Change | Result |
| --- | --- | --- |
| 1 | Baseline | Unreadable gibberish. |
| 2 | AdamW Optimizer | Actual words appear; structure improves. |
| 3 | Dropout | Better generalization; reduced overfitting. |
| **Final** | **Longer Training** | **Coherent Shakespearean style and formatting.** |
