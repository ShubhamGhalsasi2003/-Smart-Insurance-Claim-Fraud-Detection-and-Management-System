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

---

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

