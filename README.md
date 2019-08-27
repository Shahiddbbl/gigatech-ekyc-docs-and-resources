# GIGA TECH eKYC Solution - Documentation & Resources

Please find all the updated resources here in this repository.

## CHANGELOG (Important)
#### Version 1.07 (Update: 27th August, 2019)

##### Implemented changes
###### A. POST Customer Registration : Step 1 - NID Upload
       URL: /agent/customer-registration/?step=1&crop=1

Response will be changed from "id_front_url" to "id_front_image" & "id_back_url" to "id_back_image".
"id_front_image" & "id_back_image" will be base64 encoded images. Example:

"id_front_image": "data:image/png;base64,b'/9j/4AAQSkZJRgABAQEAeAB4AAD/4RUyRXhpZgAATU0AKgAAAAgABgEPAAIAAAALAAAAVgEQAAIAAAAJAAAAYgESAAMAAAABAAEAAAEyAAIAAAAUAAAAbIdpAAQAAAABA"

the response will also have "id_front_name" & "id_back_name" which will be needed for step 2.


###### B. POST Customer Registration: Step 2 - Photo & Other Information Upload
       URL: /agent/customer-registration/?step=2

Change "id_front_url" to "id_front_name" & "id_back_url" to "id_back_name".
The "id_front_name" & "id_back_name" will be from the response of Step 1.

###### C. POST Customer Registration: Step 2 - Photo & Other Information Upload
       URL: /agent/customer-registration/?step=2

In the success response for "status" : "passed" or "failed":

"applicantPhoto_from_card" will now be be an base64 encoded image.
"applicantPhoto_from_app" will now be be an base64 encoded image.

## FAQs
####Aspect Ration of NID?
--> 16:10
####NID Photo Resolution requirement?
---> Minimum 1000px in width (If cropped along the NID borders).
####Should we do anything with the DOB format?
--> No. Recieve the response in Step 1, and send it back in Step 2.
####Why do we need the send some data from Step 1 to Step 2 again?
--> Step 1 is stateless so, we don't maintain a DB till Step 2. We avoided unnecessary overhead.
####How do you send the image to us?
--> Base64 encoded image. Example:
```
"id_front_image": "data:image/png;base64,/9j/4AAQSkZJRgnhITNSAAAUAAABapICAAUAAAABAAABfpsfsdfsscfss3DFFFGDF"
```
####What should be my image posting format?
--> Can be jpg, jpeg, png

####What is your given image format in the responses?
---> png

## Support
Please open an issue first to discuss.

## License
Copyright (c) GIGA TECH Limited

Permission is hereby granted, free of charge, to the selected Banks/Organizations obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software with restriction, including limitation of the rights to use only for the BFIU initiated Pilot Program to trial eKYC.


Any copy, modify, merge, publish, distribute, sub-license, and/or sell copies of the Software is prohibited.

Permission of use is only for the persons associated to the Piloting Banks/Organizations to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE AND NON INFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
