# HamrahDoctor interview task

## Description

Design and develop a client for this service. 
Our example service is responsible for uploading images.
Design and develop a client to upload files to server by convention.
A simple UI for Start and Stop the process and logging the entire process is enough but each UI/UX feature and visual beauties are count as a score.
Each feature you develop for this system count as a score.
for any question contact with https://t.me/suspend

## Submitting process
Please create a github repository and email the link to musavi@tuta.io or send it in Telegram to https://t.me/suspend
## The API
API Address: https://utest.rxmoein.dev


- **Registering an image**:

  - **method**: `POST`
  - **URI**: `/image`
  - **Content-Type**: `application/json`
  - **Request Body**:

    ```json
    {
      "sha256": "abc123easyasdoremi...",
      "size": 123456,
      "chunk_size": 256
    }
    ```

  - **Responses**:
    | Code                       | Description                   |
    | -------------------------- | ----------------------------- |
    | 201 Created                | Image successfully registered |
    | 409 Conflict               | Image already exists          |
    | 400 Bad Request            | Malformed request             |
    | 415 Unsupported Media Type | Unsupported payload format    |

- **Uploading an image chunk**:

  - **method**: `POST`
  - **URI**: `/image/<sha256>/chunks`
  - **Content-Type**: `application/json`
  - **Request Body**:

    ```json
    {
      "id": 1,
      "size": 256,
      "data": "8   888   , 888    Y888 888 888    ,ee 888 888 888 888 ..."
    }
    ```

  - **Responses**:
    | Code          | Description                 |
    | ------------- | --------------------------- |
    | 201 Created   | Chunk successfully uploaded |
    | 409 Conflict  | Chunk already exists        |
    | 404 Not Found | Image not found             |

- **Downloading an image**:

  - **method**: `GET`
  - **URI**: `/image/<sha256>`
  - **Accept**: `text/plain`
  - **Responses**:
    | Code          | Description                   |
    | ------------- | ----------------------------- |
    | 200 OK        | Image successfully downloaded |
    | 404 Not Found | Image not found               |

  - **Note**: This endpoint returns plain text, not JSON. It should return the whole image instead of separate chunks.

- **Errors**:

  - **Accept**: `application/json`
  - **Response body**:

    ```json
    {
      "code": "400",
      "message": "Chunk ID field is missing."
    }
    ```
