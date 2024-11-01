

This script generates a word cloud from a text file using the WordCloud library, and displays it in two versions:
1. A standard word cloud with a rectangular shape and pink background.
2. A custom-shaped word cloud based on a mask image, with words filling the shape defined by the mask.

Dependencies:
--------------
1. `nltk`: Used for tokenization and handling text data.
2. `matplotlib.pyplot`: Used for plotting and displaying the word cloud.
3. `PIL (Pillow)`: Used for loading and handling the mask image.
4. `numpy`: Used for handling the mask image as a NumPy array.
5. `wordcloud`: Used for generating the word cloud.

Instructions:
--------------
1. Upload the text file (e.g., `JaneEyre.txt`) to Google Drive.
2. Upload a mask image in `.webp` or another format to Google Drive to shape the word cloud (e.g., a heart shape).
3. Adjust the file paths to your text and mask images in Google Drive.

Code Explanation:
------------------

1. **Setup and Imports**
    - Import necessary libraries (`WordCloud`, `STOPWORDS`, `plt`, `nltk`, `Image`, `np`) for word cloud generation, plotting, and image handling.
    - Download the NLTK punkt tokenizer for word tokenization.

2. **Mount Google Drive**
    - `drive.mount('/content/drive')`: Mounts Google Drive in Google Colab to access files stored there.

3. **Load Text File**
    - Opens and reads the text file `JaneEyre.txt` from Google Drive and stores the content in the `text` variable.

4. **Generate Standard Word Cloud**
    - `WordCloud(...)`: Creates a word cloud with the following parameters:
        - `width=800`, `height=400`: Defines the size of the word cloud.
        - `background_color="pink"`: Sets the background color to pink.
        - `stopwords=set(STOPWORDS)`: Filters out common stopwords.
        - `min_font_size=10`: Sets the minimum font size for words.
    - `generate(text)`: Generates the word cloud from the loaded text.
    - `plt.imshow(wordcloud)`: Displays the standard word cloud.

5. **Load Mask Image**
    - `mask_path`: Defines the path to the mask image in Google Drive.
    - `Image.open(mask_path)`: Opens the mask image.
    - `np.array(...)`: Converts the mask image to a NumPy array, so it can be used as a mask for the word cloud.

6. **Generate Custom-Shaped Word Cloud**
    - Creates a word cloud using the mask image with additional parameters:
        - `background_color="black"`: Sets the background color to black.
        - `mask=mask_image`: Applies the custom shape defined by `mask_image`.
        - `contour_color='white'`: Adds a white outline around the mask shape.
        - `contour_width=1`: Sets the outline width.
    - `generate(text)`: Generates the custom-shaped word cloud.

7. **Display Custom-Shaped Word Cloud**
    - `plt.imshow(wordcloud, interpolation="bilinear")`: Displays the custom-shaped word cloud using bilinear interpolation for smoother text edges.
    - `plt.axis("off")`: Removes axes for a cleaner view.
    - `plt.show()`: Displays the plot.

Parameters:
------------
- `width`, `height`: Dimensions of the word cloud.
- `background_color`: Background color of the word cloud.
- `stopwords`: Set of words to exclude from the word cloud.
- `min_font_size`: Minimum font size for the words.
- `mask`: Shape mask for custom word cloud.
- `contour_color`, `contour_width`: Color and thickness of the outline around the masked shape.
