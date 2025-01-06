## API Documentation

### Base URL:
[http://0.0.0.0:6003/docs](http://0.0.0.0:6003/docs)

### Endpoint: POST `/api/predict`

#### Description:
This endpoint processes uploaded image files or Base64-encoded image data for forensic analysis. It returns detailed insights about the image, including potential tampering and object detection results.

### Request Body:

- `multipart/form-data`
    - `image_file`: (`string($binary), optional`) - The image file. Default None.
    - `base64_data`: (`string`, optional) - Base64 data of the image. Default None.
    - `file_name`: (`string`, optional) - filename for the image.
    - `transaction_id`: (`string`, required) - A unique identifier for the transaction.

- **Note**:

    Either **`image_file`** or **`base64_data`** must be provided, but not both; omitting or providing both will result in a error message.

---

### Responses:

#### **`200 OK`**: Successful Response
    - Media Type: `application/json`
    - Example Value:
        ```json
        {
            "respcode": 200,
            "respdesc": "Success",
            "data":  {
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
        }
        ```

#### **`4XX` and `5XX` Error Codes**: Common Error Responses
- **Media Type**: `application/json`
- **Example for validation errors**:
    ```json
    {
        "respcode": 422,
        "respdesc": "Validation error details",
        "data": null
    }
    ```
- **Example for other error codes**:
    ```json
    {
        "respcode": 500,
        "respdesc": "Internal server error",
        "data": null
    }
    ```

#### Usage:

To use this endpoint, you can either upload an image file directly or provide the image data as Base64 code. Additionally, you can optionally provide a filename and a required transaction ID for tracking purposes. Upon successful processing, the endpoint will return a JSON response containing the forensic analysis results.
