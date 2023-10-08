## API Documentation

### Base URL:
[http://0.0.0.0:6003/docs](http://0.0.0.0:6003/docs)

### Endpoint: POST `/api/predict`

#### Description:
This endpoint handles file uploads as well as Base64 code processing to perform forensic checking on the provided image data.

#### Parameters:

- `file_data` (type: `UploadedFile`, optional): The uploaded file object. Defaults to None.
- `base64_data` (type: `Base64Code`, optional): The Base64 code object. Defaults to None.
- `file_name` (type: `string`, optional): An optional filename for the uploaded image. 
- `transaction_id` (type: `string`, required): A unique identifier for the transaction.

#### Request Body:

- `multipart/form-data`
    - `image_file`: `string($binary)` - The image file. Optional. Default None.
    - `base64_data`: `string` - Base64 data of the image. Default None.
    - `file_name`: `string` - Optional filename for the image.
    - `transaction_id`: `string` - A unique identifier for the transaction. Required.

#### Responses:

- `200 OK`: Successful Response
    - Media Type: `application/json`
    - Example Value:
        ```json
        {
          "label": "tampered",
          "data_stats": {
            "mask_percentage": 0.8594512939453125,
            "img_width": 512,
            "img_height": 512,
            "total_pixels": 262144,
            "total_non_zero_pixels": 2253
          },
          "transaction_id": "1234",
          "out_mask": "base-64-data",
          "out_color_mask": "base-64-data",
          "doc_integrity_verification_result": {
            "is_logo_detected": true,
            "is_flag_detected": true,
            "is_hologram_detected": true,
            "is_crop_detected": false,
            "is_barcode_detected": false,
            "logo_detection_confidence": 0.9630905389785767,
            "flag_detection_confidence": 0.9408931136131287,
            "hologram_detection_confidence": 0.9314528107643127,
            "spiral_detection_confidence": 0.6021785736083984,
            "is_spiral_lines_detected": false
          }
        }
        ```

- `422 Unprocessable Entity`: Validation Error
    - Media Type: `application/json`
    - Example Value:
        ```json
        {
            "detail": [
                {
                    "loc": [
                        "string",
                        0
                    ],
                    "msg": "string",
                    "type": "string"
                }
            ]
        }
        ```

#### Usage:

To use this endpoint, you can either upload an image file directly or provide the image data as Base64 code. Additionally, you can optionally provide a filename and a required transaction ID for tracking purposes. Upon successful processing, the endpoint will return a JSON response containing the forensic analysis results.
