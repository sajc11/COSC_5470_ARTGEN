# Real-Time Art Generator from Music
## Project Overview
This project demonstrates how to generate surrealist and abstract art in from audio spectogram inputs, such as:

It leverages a self-trained Convolutional Neural Network (CNN) to predict mood metrics (valence and energy) from music spectrograms, which are then used to modulate a latent vector as a condition to a Generative Adversarial Network (GAN) generator, producing corresponding surrealist/abstract artwork. 
The project comprises several Jupyter notebooks including ```CNN_Training.ipynb``` and ```GAN_Training.ipynb``` to train the models and ```GAN_Future_Implementations.ipynb``` which holds future development improvements, each covering different aspects of the workflow.

## Features
1. **CNN Training:** The CNN_Training.ipynb notebook trains a Convolutional Neural Network model to predict mood metrics (valence and energy) from music spectrograms.
   The CNN was trained on metadata and spectographs from more than 400 popular songs from a wide range of genres.
   ![Blue Sky Black Death - Gold In Gold Out](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/69afd556-55d7-4742-ae95-91a866b63c49)![Accept - Stalingrad](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/198dd3a1-ce0c-475e-9ec9-595b86f0d09f)![65daysofstatic - Tiger Girl](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/9acca507-fe3c-477d-a8e0-a9eb774da3e2)

3. **GAN Training:** The GAN_Training.ipynb notebook trains a GAN generator to synthesize surrealist art from latent vectors, including training loops, visualization tools, and model checkpoints.
4. The GAN was trained on over 9000 images of Abstract and Surrealist Art
   ![Screenshot 2024-05-01 at 9 22 20 PM](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/2086b4d2-2f64-412d-96cf-f360415bbb10)
   ![Screenshot 2024-05-01 at 9 22 39 PM](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/8cf4a1f1-c14c-454a-8467-5d6647c258c6)

6. **Real-Time Art Generation:** The GAN_Future_Implementations.ipynb notebook implements the real-time art generator:
      * **Audio Recording:** Provides an HTML interface to record audio directly in the notebook, saving recordings as WebM files and converting them to WAV format.
      * **Spectrogram Generation:** Converts the recorded audio into Mel spectrograms using the Librosa library.
      * **Mood Prediction:** Uses the pre-trained CNN model to predict mood metrics (valence and energy) from the spectrogram.
      * **Art Generation:** Modulates a latent vector with the mood metrics, passing it to the GAN generator to produce corresponding artwork.
      * **Visualization:** Displays the generated artwork in real time on a Matplotlib plot, updating dynamically as new audio is recorded and processed.

## Results
### Spectrogram-to-Art Generation:
Here are some examples of the abstract-surrealist art generated from music spectrograms:
![download-1](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/41c10228-7ce5-48c9-85d5-0ce015ea862a)
![download-2](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/3c2c40ca-8cbc-4664-8bfe-0ba507ae514f)
![download](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/5c68abb2-7600-459f-b27c-e320dbb1c079)

These images illustrate the diversity of outputs generated by the GAN model, based on various spectrogram inputs.

## Conclusion:
The results demonstrate the potential of combining audio processing with deep learning to generate unique visual art forms.

These images illustrate the diversity of outputs generated by the GAN model, based on various spectrogram inputs.

## How to Run
1. **Clone the Repository**
     ```
      git clone https://github.com/your-username/real-time-art-generator.git
      cd real-time-art-generator
      ```
3. **Set Up the Environment**
     Ensure Python and Juptyer are installed. You can use a virtual environment for isolation. Alternatively, use Google Collab Pro
     ```
      pip install virtualenv
      virtualenv venv
      source venv/bin/activate
     ```
     Install the necessary packages:
      ```
        pip install -r requirements.txt
      ```
5. **Run the Jupyter Notebooks**
     Start Juptyer and open the desired notebook:
     ```
       jupyter notebook
     ```
     Open ```CNN_Training.ipynb``` or ```GAN_Training.ipynb``` to train the models or ```GAN_Future_Implementations.ipynb``` for real-time art generation.
     Please note that certain features within ```GAN_Future_Implementations.ipynb``` may not be available yet!

# Architecture and Workflows
1. **CNN Model:** Trained to predict mood metrics (valence and energy) from music spectrograms. The predicted metrics are used to modulate a latent vector.
2. **GAN Generator:** Takes the modulated latent vector and synthesizes surrealist art. The generator is pre-trained on a dataset of surrealist art images.
3. **Real-Time Integration:** Combines the CNN model and GAN generator in a real-time pipeline, allowing for dynamic art generation from recorded audio.

# Data Sources
* **Music Spectrograms:** Generated from various audio tracks for training the CNN model.
* **Surrealist Art Dataset:** A collection of surrealist art images used for training the GAN generator.

# Future Implementations 
The goal of further development to this code is to eventually generate a model that can continuously generate dynamic art based on some live feed of music.
We hope such results will end up looking somewhat like this:
![](https://github.com/COSC_5470_ARTGEN/resources/giphy.gif)

  Available in ```GAN_Future_Implementations.ipynb```
1. **Advanced Audio Processing:** Incorporate additional audio features, such as rhythm patterns or pitch, to enrich the input data, leading to more dynamic art generation.
2. **Web Integration:** Extend the recording interface to integrate directly with streaming platforms or music applications, allowing for continuous, dynamic art generation.
3. **Interactive Art Gallery:** Archive and display generated art in an interactive gallery, integrating with web applications or augmented reality for enhanced user experiences.