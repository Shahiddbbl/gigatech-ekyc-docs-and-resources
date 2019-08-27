# GIGA TECH eKYC Solution - Documentation & Resources

Please find all the updated resources here in this repository.

## CHANGELOG (Important)
#### Version 1.08 (Update: 28th August, 2019)

##### Implemented changes
###### A. POST Verification Status
       URL: /agent/get-verification-status/

Election Commission data is not given in the response.
NID Matching Score & DOB Matching Score is also omitted as they are already matched 100%.

New Sample Response will be:

```
{
   "status":"passed",
   "detail":{
      "nid_no":123122324243131,
      "dob":"12/12/1980",
      "applicant_name_eng":"ABDUR RAHIM",
      "applicant_name_eng_score":85,
      "applicant_name_ben":"আব্দুর রহিম",
      "applicant_name_ben_score":85,
      "father_name":"কুদ্দুসুর রহিম",
      "father_name_score":85,
      "mother_name":"রহিমা খাতুন",
      "mother_name_score":85,
      "pres_address":"বাড়ী ৩, মোহাম্মদপুর, ঢাকা",
      "pres_address_score":85,
      "textual_info_match":true,
      "applicant_photo_from_card":”data:image/png;base64,/9j/4AAQSkZJRgABAQEAeAB4AAD/4RUyRXhpZgAATU0AKgAAAAgABgEPAAIAAAALAAAAVgEQAAIAAAAJAAAAYgESAAMAAAABAAEAAAEyAAIAAAAUAAAAbIdpAAQA”,
      "applicant_photo_card_ec_match":true,
      "applicant_photo_from_app":”data:image/png;base64,/9j/4AAQSkZJRgABAQEAeAB4AAD/4RUyRXhpZgAATU0AKgAAAAgABgEPAAIAAAALAAAAVgEQAAIAAAAJAAAAYgESAAMAAAABAAEAAAEyAAIAAAAUAAAAbIdpAAQA”,
      "applicant_photo_app_ec_match":true
   }
}

``` 

###### B. GET Verification Log
       URL: /agent/get-verification-log/

Response keys got changed matching with verification log response.
Sample Response:
```
[
   {
      "mobile_number":"01716705911",
      "applicant_name_eng":"Rahim Uddin",
      "nid_no":"192323311233532",
      "submitted_on":"11/12/1989",
      "verification_status":"passed"
   },
   {
      "mobile_number":"01716705912",
      "applicant_name_eng":"Rahim Uddin",
      "nid_no":"192323311233533",
      "submitted_on":"11/12/1990",
      "verification_status":"passed"
   },

   {
      "mobile_number":"01716705913",
      "applicant_name_eng":"Rahim Uddin",
      "nid_no":"192323311233533",
      "submitted_on":"11/12/1989",
      "verification_status":"passed"
   }
]
```

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
