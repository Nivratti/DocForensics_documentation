## Dataset Composition

To train our model to recognize manipulations, we provide it with several hundred thousand images, both genuine and manipulated. Each image is paired with its ground truth mask. During the training process, the model learns to recognize patterns and subtle hints that suggest an image has been tampered with.

### Genuine Images
These are untouched, original images. The ground truth mask for these images is purely black, indicating no regions of manipulation.

### Manipulated Images
These images have undergone some form of tampering. Accompanying each manipulated image is its ground truth mask, where:

- **White regions**: Highlight areas of the image that have been altered or tampered with.
- **Black regions**: Signify areas of the image that remain untouched or genuine.
