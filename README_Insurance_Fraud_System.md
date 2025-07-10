# 🚀 Insurance Fraud Detection System

This is a full-stack real-time web application for detecting fraudulent insurance claims using machine learning and cloud deployment. The project integrates:

- ✅ Java (Spring Boot + JSP)
- ✅ Python (Flask + ML model)
- ✅ SQL (MySQL)
- ✅ AWS Cloud (EC2)

---

## 📌 Features

- Users can submit insurance claims via a web form
- Upload supporting documents (PDF or images)
- Machine Learning model (Flask API) returns fraud probability score
- Claims are stored in MySQL (locally or AWS RDS)
- Admin panel displays all claims, fraud scores, and file links

---

## 🧰 Technologies Used

| Layer       | Technology             |
|-------------|------------------------|
| Frontend    | JSP + HTML + CSS       |
| Backend     | Java Spring Boot       |
| ML Model    | Python (Flask + scikit-learn) |
| Database    | MySQL (local or AWS RDS) |
| Hosting     | AWS EC2 (Java + Flask) |

---

## 🏗️ Project Structure

```
InsuranceFraudDetectionSystem/
├── backend/        # Java Spring Boot app
│   ├── src/
│   ├── templates/
│   └── ...
├── ml_model/       # Flask API + ML model
│   ├── app.py
│   └── model.pkl
├── sql/            # MySQL schema
├── README.md
```
Here’s your entire **"Implementation Details (Code & Logic Breakdown)"** section, converted into **GitHub-compatible Markdown format**, all in **one page**, properly structured and ready to be added to your `README.md`:

---

````md
## 🧪 Implementation Details (Code & Logic Breakdown)



## **⚙️ Java (Spring Boot) – Backend Logic**

#### 📌 Form Submission Controller

```java
@PostMapping("/submit-claim")
public String submitClaim(@ModelAttribute Claim claim, @RequestParam("file") MultipartFile file) {
    claimService.save(claim); // save claim data
    double fraudScore = mlService.getFraudScore(claim); // call Flask API
    claim.setFraudScore(fraudScore);
    claimService.update(claim);
    return "redirect:/confirmation";
}
````

#### 📌 Calling Flask ML API

```java
RestTemplate restTemplate = new RestTemplate();
String url = "http://localhost:5000/predict";
HttpEntity<Claim> request = new HttpEntity<>(claim);
ResponseEntity<String> response = restTemplate.postForEntity(url, request, String.class);
```

#### 📌 JSP Form Example

```jsp
<form action="/submit-claim" method="post" enctype="multipart/form-data">
    Name: <input type="text" name="name" />
    Amount: <input type="number" name="amount" />
    Upload File: <input type="file" name="file" />
    <button type="submit">Submit</button>
</form>
```

---

### 🧠 Python (Flask + ML Model) – Fraud Detection API

#### 📌 Flask API Endpoint

```python
@app.route('/predict', methods=['POST'])
def predict():
    data = request.get_json()
    features = preprocess(data)
    score = model.predict_proba([features])[0][1]
    return jsonify({'fraud_score': float(score)})
```

#### 📌 Model Loading

```python
import joblib
model = joblib.load('model.pkl')
```

#### 📌 Preprocessing Function

```python
def preprocess(data):
    return [data['amount'], data['history'], data['region']]  # Example fields
```

---

### 🗄️ MySQL – Database (Java Integration)

#### 📌 Spring Boot Entity

```java
@Entity
public class Claim {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private double amount;
    private double fraudScore;
}
```

## 🚦 How to Run

### ✅ 1. Run ML API
```bash
cd ml_model
pip install -r requirements.txt
python app.py
```

### ✅ 2. Run Java Backend
```bash
cd backend
mvn clean install
java -jar target/insurance-fraud-backend.jar
```

---

## 🌐 URLs

- Claim Form: `http://<your-ec2-ip>:8080/claim-form`
- Admin Dashboard: `http://<your-ec2-ip>:8080/admin`
- ML API Endpoint: `http://<your-ec2-ip>:5000/predict`

---

## 🖼️ Screenshots

- 📄 Claim Form  
- 📊 Admin Dashboard (fraud score included)

See `/screenshots/` or use attached images.

---

## 📦 Deployment (AWS EC2)

Run the script:
```bash
chmod +x aws_project_setup.sh
./aws_project_setup.sh
```

---

## 📜 Author

**Shubham Ghalsasi**  
Final Year B.Tech - Cloud Computing  
MIT ADT University

For inquiries: ghalsasishubham@gmail.com

