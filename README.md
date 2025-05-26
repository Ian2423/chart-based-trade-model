# 📊 Trade Direction & Outcome Classifier

A deep learning model that predicts trade direction and expected outcome based on chart screenshots around 7:30–8:00 am (London time). Built with TensorFlow and trained using chart images and trade history.

---

## Model Purpose

- 🔍 Input: Chart image (e.g., TradingView screenshot)
- 📈 Output 1: Trade Direction — `buy` or `sell`
- 🎯 Output 2: Expected Outcome — `half & full profit`, `half profit & breakeven`, or `loss`

The model learns from both winning and losing trades, improving over time with human feedback.

---

## Architecture

- **Backbone**: MobileNetV2 (pretrained, frozen)
- **Multi-output**: One head for `direction`, one for `outcome`
- **Trained on**: CSV dataset + matching `.jpg` files

---

## Files

| File                             | Description                               |
|----------------------------------|-------------------------------------------|
| `trade_model.ipynb`              | Main notebook (training, prediction, fine-tuning) |
| `trades.csv`                 | Dataset of trades with labels             |
| `corrections.csv`               | (Optional) New trade corrections for fine-tuning |
| `trade_multi_output_model.keras`| Trained model (MobileNetV2 backbone)      |
| `label_encoder.pkl`              | Outcome label encoder                     |
| `direction_encoder.pkl`          | Direction label encoder                   |

---

## Fine-Tuning the Model

Add your real trades to `corrections.csv` using this format:

```csv
chart_image,direction_taken,label,results_pips
Screenshot_20250524_073000.jpg,buy,loss,-40
```
# How to Use
Upload your .jpg chart image to Colab

Run predict_from_chart('your_image.jpg')

Get model output: direction + expected outcome

If the model is wrong and you were right, log the trade

Periodically fine-tune or retrain the model

# Motivation
This model supports decision-making for manual traders who rely on structure and intuition. It improves with feedback, using your trade corrections as learning signals.

# Requirements
Python 3.x

TensorFlow

Scikit-learn

pandas, numpy, matplotlib, Pillow
