# nanoGPT


# Training Report: nanoGPT

This report documents the iterative improvement of a character-level GPT model trained on the Tiny Shakespeare dataset. It tracks the transition from a basic Bigram-like performance to a more coherent Transformer model.

## Version 1: Constant Learning Rate (Baseline)

* **Parameters:** Learning Rate = 0.05, Epochs = 1000
* **Optimizer:** SGD (Standard Gradient Descent)
* **Observation:** The model struggles with basic English structure. It outputs mostly gibberish with frequent non-existent words.

<img width="669" height="440" alt="image" src="https://github.com/user-attachments/assets/cd4c76df-5a20-4e1b-a86c-a6d17e81a480" />




**Generated Output:**

> "The f hucheme uts liBumRove ainghe f my d shofathe tosh t, beis
Pormy ope shill y mo ven pus'lomy, f ots f ROfoumise bes spe t apa thttheg,
t, ch; sorite t t,
By
Bu sofadee hiswevert tt lake y tore y s isterd, a ay
Artheren til? s I mbithe IO andacodle, ho ined o ave hangb alt
Thayam. viof cage, Itoold covO tdese; a it ie f, fane, w's d on:

I tincke fuf I pincen y u, epeman gead cr bclea sthe d co wa
Ta ionuthalo.
Whatoke d huce t tl d chis m
wond o, weequearthetratFothe s h.

Serof?
BUKE thinde RW"

---

## Version 2: Switching to AdamW

* **Parameters:** Learning Rate = 3e-4, Epochs = 1000
* **Optimizer:** AdamW
* **Observation:** Significant improvement. By using the AdamW optimizer (which adapts the learning rate for each parameter), the model begins to recognize character names (KING RICHARD II) and uses actual English words, though the sentences lack logical cohesion.

<img width="665" height="438" alt="image" src="https://github.com/user-attachments/assets/f224e596-e613-49ae-9fd3-9f4bf6d7d89a" />




**Generated Output:**

> "The kaus my caate shall to heavinous come. The curse to the tonguest place are make..."

---

## Version 3: Introducing Dropout

* **Parameters:** Epochs = 1000, Optimizer = AdamW, Dropout = 0.1
* **Observation:** Dropout was added to prevent the model from memorizing the training data (overfitting). While the 1000-epoch output is similar to Version 2, the model is now better prepared for longer training sessions without becoming "rigid."

<img width="666" height="437" alt="image" src="https://github.com/user-attachments/assets/5381028f-6b5c-4bae-9a8a-a302e2c5f7d6" />




**Generated Output:**

> "LADY: A shadand sriss verced-mes, not Rome you leame..."

---

## Final Version: Optimized Hyperparameters & Extended Training

* **Parameters:** Epochs = 5000, Optimized Head Size/Embedding, Dropout = 0.2
* **Observation:** This is the most "literary" version. After 5000 epochs, the model understands dialogue formatting (Character Name followed by text), basic punctuation, and simple sentence structures. It mimics the "rhythm" of Shakespeare effectively.

<img width="677" height="437" alt="image" src="https://github.com/user-attachments/assets/fa5e0db1-cfeb-467a-85af-5d11782df48d" />



**Generated Output:**

> "AUTOLYCUS: As traitor, my lord's word; sudden, I tout unltoget o' The delivery? Common neither."

---

## Summary of Findings

| Version | Key Change | Result |
| --- | --- | --- |
| 1 | Baseline | Unreadable gibberish. |
| 2 | AdamW Optimizer | Actual words appear; structure improves. |
| 3 | Dropout | Better generalization; reduced overfitting. |
| **Final** | **Longer Training** | **Coherent Shakespearean style and formatting.** |
