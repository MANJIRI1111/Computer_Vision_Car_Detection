# Computer_Vision_Car_Detection
1.	Introduction
Urbanization has led to increased vehicular traffic, creating a pressing demand for efficient parking management systems. Traditional approaches rely heavily on human intervention or outdated technologies, resulting in inefficiencies and user inconvenience. This project integrates computer vision for real-time detection and counting of cars with time series analysis to forecast parking lot trends. By leveraging these technologies, the system provides a scalable, automated solution to optimize parking space management.
2. Problem Statement
Manual or traditional systems for monitoring parking lot occupancy are prone to human error and inefficiencies. Issues such as unutilized spaces, overbooking, and lack of real-time data significantly reduce parking lot efficiency. The absence of predictive analysis also prevents administrators from planning based on historical trends. Therefore, an automated system capable of detecting car occupancy and predicting future usage is crucial.

3. Objectives
  The primary objectives of the project are:
  1.	To develop an automated system that uses computer vision to detect and count cars in real-time.
  2.	To store detection data for historical analysis and trend extraction.
  3.	To utilize time series models to predict future occupancy, enabling better management decisions.
  4.	To ensure the system is robust to variations in weather, lighting, and environmental conditions.

4. Methodology
Dataset:
The dataset utilized is CNRPark, comprising a total of 3,178 images captured over a four-month period at various time intervals. The images were collected using four cameras positioned at different angles within a single parking area, providing diverse perspectives for analysis. A separate CSV file was created to record the datetime and the number of cars detected in each frame or time interval. Eg. of the data sample:
 

Computer Vision Techniques
Model Used: Faster R-CNN + InceptionResNet V2
Faster R-CNN is a state-of-the-art object detection model. It uses a Region Proposal Network (RPN) to generate potential object regions, followed by a classifier to refine and classify these regions. This makes it both accurate and efficient for real-time tasks.
InceptionResNet V2 is a deep convolutional neural network that combines the strengths of the Inception architecture (multi-scale convolution) and ResNet (residual learning). This backbone enhances feature extraction capabilities, improving detection accuracy for complex images.
Preprocessing:
○	Images are resized to a consistent resolution.
○	Augmentation techniques like rotation, flipping, and contrast adjustments are applied to improve robustness.
Detection Process:
○	Input images are fed into the Faster R-CNN model.
○	The RPN identifies regions of interest (ROIs) likely to contain cars.
○	The classifier assigns labels with number of cars and refines bounding box positions in the image.
Output:
The model outputs bounding boxes around detected cars and the number of cars detected in each image as shown in the picture below:   

Time Series Analysis
Model Used: ARIMA (AutoRegressive Integrated Moving Average)
ARIMA is well-suited for modeling time series data with trends and seasonality, such as hourly or daily car counts in parking lots.
1.	Data Preparation:
The labeled dataset (CSV file) containing timestamps and car counts was aggregated into regular intervals (hourly, daily).
Stationarity was tested using the Augmented Dickey-Fuller (ADF) test. Non-stationary data was differenced.
2.	Model Training:
Parameters (p, d, q) for ARIMA were selected using the Akaike Information Criterion (AIC).
 
3.	Validation:
Residuals of the model were analyzed to ensure a good fit.
 
4.	Prediction:
Future car counts were forecasted, including confidence intervals.
 

5. Implementation
Tools and Technologies:
●	Programming Languages: Python
●	Frameworks: TensorFlow (for Faster R-CNN), statsmodels (for ARIMA).
●	Libraries: OpenCV, pandas, matplotlib, seaborn.
●	Hardware: NVIDIA GPU for model training and inference.
Steps performed:
1.	Train the Faster R-CNN model with the labeled dataset.
2.	Test the model on new parking lot images.
3.	Export the car count and timestamp data to a CSV file.
4.	Train the ARIMA model on the exported data to identify trends and make predictions.
5.	Integrated the process of detection of cars from the image into UI using..

7. Challenges and Limitations
●	Environmental Conditions: Poor lighting and weather reduced detection accuracy.
●	Occlusion: Cars parked close together sometimes caused false negatives.
●	Dataset Limitations: Limited data diversity affected generalizability to all parking lot configurations.
8. Future Scope
●	Hybrid Systems: Combine computer vision with IoT sensors to cross-verify results.
9. Conclusion
The project successfully integrated Faster R-CNN with InceptionResNet V2 for car detection and ARIMA for occupancy forecasting. Using a custom-labeled dataset with timestamps and car counts, the system achieved high accuracy in both detection and prediction tasks. The framework offers a scalable solution for automated parking lot management, with potential for further enhancements.



