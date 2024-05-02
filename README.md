# Real-Time Art Generator from Music
Developers: Sophia (Alivia) Castor, Eli Kerstein

Net IDs: soc11, ewk33

## Project Overview
This project demonstrates how to generate surrealist and abstract art from audio spectrogram inputs, such as:

It leverages a self-trained Convolutional Neural Network (CNN) to predict mood metrics (valence and energy) from music spectrograms, which are then used to modulate a latent vector as a condition to a Generative Adversarial Network (GAN) generator, producing corresponding surrealist/abstract artwork. 
The project comprises several Jupyter notebooks including ```CNN_Training.ipynb``` and ```GAN_Training.ipynb``` to train the models and ```GAN_Future_Implementations.ipynb``` which holds future development improvements, each covering different aspects of the workflow.

This repo contains the full dataset used as well as some of our training graphs, logs, and snapshots of our final results-- aka the abstract images generated using the GAN from the CNN and spectrograph conditions. Additionally, this repo contains the ```.ipnyb``` files for all of the code used to conduct this project. Each file contains descriptions and inline code comments of the goals and the functions of the code within the respective file. Unfortunately, we are unable to upload the pre-trained and saved models for the CNN and GAN due to their large file size! 

Within the repo, under ```resources/presentation_ppt```, there is a PDF to our presentation slides for this project.

## Features
1. **Generating Spectrograms:**
   The Generate_Spectrogtam.ipynb takes in each mp3 file from the dataset of songs, and samples a 30-second clip. We sample only a segment of the song as it is very computationally intensive to convert the entire audio track. We then use the fast fourier transform to create a spectrographic representation of each audio clip, giving valuable information about the prevalent frequencies in the track as well as the temporal dynamics.
   * The data gathered from this step is stored in the spectrogram folder
3. **Obtaining Spotify Data:** 
   The Spotify_Data.ipynb uses the Spotify API to get the metadata corresponding to each song. We get the valence, energy, and genre, and write each one to a spreadsheet that will act as labels for the spectrograms. If a song doesn't have sufficient metadata, then we don't put it in the spreadsheet.
   * The data gathered from this step is stored in the song_metadata.csv.
5. **CNN Training:** The CNN_Training.ipynb notebook trains a Convolutional Neural Network model to predict mood metrics (valence and energy) from music spectrograms.
   The CNN was trained on metadata and spectrographs from more than 400 popular songs from a wide range of genres.
   ![Blue Sky Black Death - Gold In Gold Out](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/69afd556-55d7-4742-ae95-91a866b63c49)![Accept - Stalingrad](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/198dd3a1-ce0c-475e-9ec9-595b86f0d09f)![65daysofstatic - Tiger Girl](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/9acca507-fe3c-477d-a8e0-a9eb774da3e2)
6. **GAN Training:** The GAN_Training.ipynb notebook trains a GAN generator to synthesize surrealist art from latent vectors, including training loops, visualization tools, and model checkpoints.
   * The GAN was trained on over 9000 images of Abstract and Surrealist Art
   ![Screenshot 2024-05-01 at 9 22 20 PM](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/2086b4d2-2f64-412d-96cf-f360415bbb10)
   ![Screenshot 2024-05-01 at 9 22 39 PM](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/8cf4a1f1-c14c-454a-8467-5d6647c258c6)
7. **Real-Time Art Generation:** The GAN_Future_Implementations.ipynb notebook implements the real-time art generator:
      * **Audio Recording:** Provides an HTML interface to record audio directly in the notebook, saving recordings as WebM files and converting them to WAV format.
      * **Spectrogram Generation:** Converts the recorded audio into Mel spectrograms using the Librosa library.
      * **Mood Prediction:** Uses the pre-trained CNN model to predict mood metrics (valence and energy) from the spectrogram.
      * **Art Generation:** Modulates a latent vector with the mood metrics, passing it to the GAN generator to produce corresponding artwork.
      * **Visualization:** Displays the generated artwork in real-time on a Matplotlib plot, updating dynamically as new audio is recorded and processed.

## Results
### Spectrogram-to-Art Generation:
Here are some examples of the abstract-surrealist art generated from music spectrograms:
![download-1](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/41c10228-7ce5-48c9-85d5-0ce015ea862a)
![download-2](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/3c2c40ca-8cbc-4664-8bfe-0ba507ae514f)
![download](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/5c68abb2-7600-459f-b27c-e320dbb1c079)

These images illustrate the diversity of outputs generated by the GAN model, based on various spectrogram inputs, representing varying music genres including pop, folk, and rap music respectively.

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
  * The corresponding jupyter notebooks: ```Spotify_Data.ipynb``` and ```Generate_Spectrogram.ipynb``` used to obtain this data can be found within the ```/src``` folder.
  * Additionally, the spectrograph dataset, entitled ```/spectrograms```, and corresponding metadata csv, ```song_metadata.csv``` can be found within the ```/dataset``` folder of this github.
* **Abstract/Surrealist Art Dataset:** A collection of abstract & surrealist art images used for training the GAN generator.
   * The folder ```AI_Abstract_Surrealism_DataSet``` contains all art data used in this project, and can be found within the ```/dataset``` folder.

# Future Implementations 
The goal of further development to this code is to eventually generate a model that can continuously generate dynamic art based on some live feed of music.
We hope such results will end up looking somewhat like this:

![giphy](https://github.com/sajc11/COSC_5470_ARTGEN/assets/117310329/0b90807e-b25a-4ab2-872a-7d65df2cda30)

  Additional code updates will be available in ```GAN_Future_Implementations.ipynb```
1. **Advanced Audio Processing:** Incorporate additional audio features, such as rhythm patterns or pitch, to enrich the input data, leading to more dynamic art generation.
2. **Web Integration:** Extend the recording interface to integrate directly with streaming platforms or music applications, allowing for continuous, dynamic art generation.
3. **Interactive Art Gallery:** Archive and display generated art in an interactive gallery, integrating with web applications or augmented reality for enhanced user experiences.

## Reference Papers
Our main references for this project are as follows:

MeloHarmony: Exploring Emotion in Crafting AI-Generated Music with Generative Adversarial Network Powered Harmony-
 https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4575257 

Generative artificial intelligence, human creativity, and art 
https://academic.oup.com/pnasnexus/article/3/3/pgae052/7618478

Transparency in Music-Generative AI: A Systematic Literature Review
https://www.researchsquare.com/article/rs-3708077/v1



