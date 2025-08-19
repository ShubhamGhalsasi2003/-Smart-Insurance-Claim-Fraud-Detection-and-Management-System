![Frontend](https://img.shields.io/badge/Frontend-JSP-black) ![Python](https://img.shields.io/badge/Frontend-HTML-blue) ![SQL](https://img.shields.io/badge/Frontend-CSS-darkgreen) 

![Backend](https://img.shields.io/badge/Backend-Java(Springboot)-black)
 
![ML](https://img.shields.io/badge/MLModel-Python(Flask+Scikitlearn)-black)

![Datebase](https://img.shields.io/badge/Database-Mysql(AWSRDS)-black)

![Hosting](https://img.shields.io/badge/Hosting-AWSEC2-black)

![Completed](https://img.shields.io/badge/Status-Completed-success)  



##  Problem Statement
Insurance fraud costs companies billions each year.  
Traditional claim verification processes are **time-consuming, error-prone, and costly**.  

➡️ This project provides a **real-time fraud detection system** using **Machine Learning + Cloud Deployment**, making the claim process more **efficient, scalable, and secure**.  

---

##  Features
-  **User Claim Submission** via a web form (JSP + Spring Boot).  
-  Upload **supporting documents** (PDF/images).  
-  **Machine Learning model (Flask API)** predicts fraud probability score.  
-  All claims stored in **MySQL (local or AWS RDS)**.  
-  **Admin Dashboard** for viewing claims, fraud scores, and file links.  
-  Hosted on **AWS EC2** for scalability.  

---

##  Technologies Used

| Layer       | Technology Used               |
|-------------|-------------------------------|
| Frontend    | JSP + HTML + CSS              |
| Backend     | Java (Spring Boot)            |
| ML Model    | Python (Flask + scikit-learn) |
| Database    | MySQL (local / AWS RDS)       |
| Hosting     | AWS EC2                       |

---

##  Project Structure

InsuranceFraudDetectionSystem/
├── backend/        # Java Spring Boot app
│   ├── src/
│   ├── templates/
│   └── ...
├── ml\_model/       # Flask API + ML model
│   ├── app.py
│   └── fraud\_model.pkl
├── sql/            # MySQL schema
├── README.md


##  Implementation Details (Code & Logic Breakdown)

### **1️ Java (Spring Boot) – Backend Logic**

 **Form Submission Controller**
java
@PostMapping("/submit-claim")
public String submitClaim(@ModelAttribute Claim claim, @RequestParam("file") MultipartFile file) {
    claimService.save(claim); // save claim data
    double fraudScore = mlService.getFraudScore(claim); // call Flask API
    claim.setFraudScore(fraudScore);
    claimService.update(claim);
    return "redirect:/confirmation";
}

**Calling Flask ML API**

java
RestTemplate restTemplate = new RestTemplate();
String url = "http://localhost:5000/predict";
HttpEntity<Claim> request = new HttpEntity<>(claim);
ResponseEntity<String> response = restTemplate.postForEntity(url, request, String.class);

 **JSP Claim Form**

html
<form action="/submit-claim" method="post" enctype="multipart/form-data">
    Name: <input type="text" name="name" />
    Amount: <input type="number" name="amount" />
    Upload File: <input type="file" name="file" />
    <button type="submit">Submit</button>
</form>


### **2️ Python (Flask + ML Model) – Fraud Detection API**

 **Flask Endpoint**

python
@app.route('/predict', methods=['POST'])
def predict():
    data = request.get_json()
    features = preprocess(data)
    score = model.predict_proba([features])[0][1]
    return jsonify({'fraud_score': float(score)})


**Model Loading**

python
import joblib
model = joblib.load('fraud_model.pkl')


**Preprocessing Function**

python
def preprocess(data):
    return [data['amount'], data['history'], data['region']]  # Example fields



### **3️ MySQL Database – Java Integration**

 **Spring Boot Entity**

java
@Entity
public class Claim {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private double amount;
    private double fraudScore;
}


##  How to Run Locally

**Step 1 – Run ML API**

bash
cd ml_model
pip install -r requirements.txt
python app.py

**Step 2 – Run Java Backend**

bash
cd backend
mvn clean install
java -jar target/insurance-fraud-backend.jar



##  Screenshots

*  Claim Form UI
*  Admin Dashboard with Fraud Scores
  
<img width="1024" height="1024" alt="3f7cca49-dd36-4f98-bb42-2b36998adce2" src="https://github.com/user-attachments/assets/595e7665-daa1-4d0e-b2d1-c73d2336df77" />
<img width="1410" height="763" alt="89b2a810-0858-422d-b86d-f079c235ec02" src="https://github.com/user-attachments/assets/f81d60d4-4495-4f3c-9cca-6d2407b76f45" />
<img width="1536" height="1024" alt="2a91e642-dea1-4c95-84c4-1e87071bc0d9" src="https://github.com/user-attachments/assets/0d1cac50-0a7b-4776-8de1-4316322f53cd" />



##  Author

**Shubham Ghalsasi**
 Final Year B.Tech – Cloud Computing
 MIT ADT University
 
    🌐 GitHub Profile
    💼 LinkedIn Profile


📧 Email: [ghalsasishubham@gmail.com](mailto:ghalsasishubham@gmail.com)
