

## **Health_AI System Architecture**

```
┌────────────────────────────────────────────────────────────────────────────┐
│                           PRESENTATION LAYER                                │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌─────────────────┐  ┌──────────────────┐  ┌─────────────────────────┐  │
│  │  Patient Portal │  │  Doctor Portal   │  │    Admin Portal         │  │
│  ├─────────────────┤  ├──────────────────┤  ├─────────────────────────┤  │
│  │ • Registration  │  │ • Registration   │  │ • User Management       │  │
│  │ • Login         │  │ • Dashboard      │  │ • System Overview       │  │
│  │ • Dashboard     │  │ • Appointments   │  │                         │  │
│  │ • Appointments  │  │ • Prescriptions  │  │                         │  │
│  │ • Profile       │  │ • Video Call     │  │                         │  │
│  │ • ML Predictions│  │                  │  │                         │  │
│  │ • Prescriptions │  │                  │  │                         │  │
│  │ • Video Call    │  │                  │  │                         │  │
│  └─────────────────┘  └──────────────────┘  └─────────────────────────┘  │
│                                                                              │
│  Templates: HTML + CSS (style.css) + JavaScript (script.js)                │
└────────────────────────────────────────────────────────────────────────────┘
                                     │
                                     ▼
┌────────────────────────────────────────────────────────────────────────────┐
│                          APPLICATION LAYER (Flask)                          │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌───────────────────────────────────────────────────────────────────────┐ │
│  │                        Core Application (app.py)                       │ │
│  └───────────────────────────────────────────────────────────────────────┘ │
│                                                                              │
│  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────────────┐ │
│  │  Authentication  │  │   Appointment    │  │   Prescription           │ │
│  │     Module       │  │    Management    │  │    Management            │ │
│  ├──────────────────┤  ├──────────────────┤  ├──────────────────────────┤ │
│  │ • User Login     │  │ • Book           │  │ • Generate PDF           │ │
│  │ • Registration   │  │ • Approve/Reject │  │ • Medicine List          │ │
│  │ • Session Mgmt   │  │ • Status Track   │  │ • View/Download          │ │
│  │ • Role-Based     │  │ • Notifications  │  │                          │ │
│  └──────────────────┘  └──────────────────┘  └──────────────────────────┘ │
│                                                                              │
│  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────────────┐ │
│  │  ML Prediction   │  │  Communication   │  │   Content Management     │ │
│  │     Engine       │  │     Module       │  │       Module             │ │
│  ├──────────────────┤  ├──────────────────┤  ├──────────────────────────┤ │
│  │ • Disease Pred.  │  │ • Email Service  │  │ • Blogs                  │ │
│  │ • Brain Tumor    │  │ • Video Call     │  │ • Privacy Policy         │ │
│  │ • Lung Cancer    │  │ • Notifications  │  │ • Mental Health          │ │
│  │ • Pneumonia      │  │                  │  │                          │ │
│  │ • Cataract       │  │                  │  │                          │ │
│  └──────────────────┘  └──────────────────┘  └──────────────────────────┘ │
│                                                                              │
└────────────────────────────────────────────────────────────────────────────┘
                │                         │                        │
                ▼                         ▼                        ▼
┌──────────────────────┐  ┌────────────────────────┐  ┌─────────────────────┐
│   DATA LAYER         │  │  ML MODELS LAYER       │  │  EXTERNAL SERVICES  │
├──────────────────────┤  ├────────────────────────┤  ├─────────────────────┤
│                      │  │                        │  │                     │
│  ┌────────────────┐ │  │  ┌──────────────────┐ │  │  ┌───────────────┐ │
│  │ SQLite Database│ │  │  │ Decision Tree    │ │  │  │ Flask-Mail    │ │
│  │  (database.db) │ │  │  │ Classifier       │ │  │  │ (SMTP/Gmail)  │ │
│  ├────────────────┤ │  │  │ (Disease Pred.)  │ │  │  └───────────────┘ │
│  │ • User Table   │ │  │  └──────────────────┘ │  │                     │
│  │ • Appointment  │ │  │                        │  │  ┌───────────────┐ │
│  │   Table        │ │  │  ┌──────────────────┐ │  │  │ ReportLab     │ │
│  └────────────────┘ │  │  │ CNN Models       │ │  │  │ (PDF Gen)     │ │
│                      │  │  │ (Brain Tumor,    │ │  │  └───────────────┘ │
│  ┌────────────────┐ │  │  │  Pneumonia,      │ │  │                     │
│  │ Training Data  │ │  │  │  Lung Cancer)    │ │  │                     │
│  │ • Training.csv │ │  │  └──────────────────┘ │  │                     │
│  │ • Testing.csv  │ │  │                        │  │                     │
│  └────────────────┘ │  │  Notebooks:            │  │                     │
│                      │  │  • brain_tumor_        │  │                     │
│  ┌────────────────┐ │  │    detection.ipynb     │  │                     │
│  │ Static Files   │ │  │  • disease-            │  │                     │
│  │ • Images       │ │  │    prediction.ipynb    │  │                     │
│  │ • PDFs         │ │  │  • lung-cancer-        │  │                     │
│  │ • Prescriptions│ │  │    prediction.ipynb    │  │                     │
│  └────────────────┘ │  │  • pneumonia-          │  │                     │
│                      │  │    detection.ipynb     │  │                     │
└──────────────────────┘  └────────────────────────┘  └─────────────────────┘

┌────────────────────────────────────────────────────────────────────────────┐
│                           PRESENTATION LAYER                                │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌─────────────────┐  ┌──────────────────┐  ┌─────────────────────────┐  │
│  │  Patient Portal │  │  Doctor Portal   │  │    Admin Portal         │  │
│  ├─────────────────┤  ├──────────────────┤  ├─────────────────────────┤  │
│  │ • Registration  │  │ • Registration   │  │ • User Management       │  │
│  │ • Login         │  │ • Dashboard      │  │ • System Overview       │  │
│  │ • Dashboard     │  │ • Appointments   │  │                         │  │
│  │ • Appointments  │  │ • Prescriptions  │  │                         │  │
│  │ • Profile       │  │ • Video Call     │  │                         │  │
│  │ • ML Predictions│  │                  │  │                         │  │
│  │ • Prescriptions │  │                  │  │                         │  │
│  │ • Video Call    │  │                  │  │                         │  │
│  └─────────────────┘  └──────────────────┘  └─────────────────────────┘  │
│                                                                              │
│  Templates: HTML + CSS (style.css) + JavaScript (script.js)                │
└────────────────────────────────────────────────────────────────────────────┘
                                     │
                                     ▼
┌────────────────────────────────────────────────────────────────────────────┐
│                          APPLICATION LAYER (Flask)                          │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌───────────────────────────────────────────────────────────────────────┐ │
│  │                        Core Application (app.py)                       │ │
│  └───────────────────────────────────────────────────────────────────────┘ │
│                                                                              │
│  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────────────┐ │
│  │  Authentication  │  │   Appointment    │  │   Prescription           │ │
│  │     Module       │  │    Management    │  │    Management            │ │
│  ├──────────────────┤  ├──────────────────┤  ├──────────────────────────┤ │
│  │ • User Login     │  │ • Book           │  │ • Generate PDF           │ │
│  │ • Registration   │  │ • Approve/Reject │  │ • Medicine List          │ │
│  │ • Session Mgmt   │  │ • Status Track   │  │ • View/Download          │ │
│  │ • Role-Based     │  │ • Notifications  │  │                          │ │
│  └──────────────────┘  └──────────────────┘  └──────────────────────────┘ │
│                                                                              │
│  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────────────┐ │
│  │  ML Prediction   │  │  Communication   │  │   Content Management     │ │
│  │     Engine       │  │     Module       │  │       Module             │ │
│  ├──────────────────┤  ├──────────────────┤  ├──────────────────────────┤ │
│  │ • Disease Pred.  │  │ • Email Service  │  │ • Blogs                  │ │
│  │ • Brain Tumor    │  │ • Video Call     │  │ • Privacy Policy         │ │
│  │ • Lung Cancer    │  │ • Notifications  │  │ • Mental Health          │ │
│  │ • Pneumonia      │  │                  │  │                          │ │
│  │ • Cataract       │  │                  │  │                          │ │
│  └──────────────────┘  └──────────────────┘  └──────────────────────────┘ │
│                                                                              │
└────────────────────────────────────────────────────────────────────────────┘
                │                         │                        │
                ▼                         ▼                        ▼
┌──────────────────────┐  ┌────────────────────────┐  ┌─────────────────────┐
│   DATA LAYER         │  │  ML MODELS LAYER       │  │  EXTERNAL SERVICES  │
├──────────────────────┤  ├────────────────────────┤  ├─────────────────────┤
│                      │  │                        │  │                     │
│  ┌────────────────┐ │  │  ┌──────────────────┐ │  │  ┌───────────────┐ │
│  │ SQLite Database│ │  │  │ Decision Tree    │ │  │  │ Flask-Mail    │ │
│  │  (database.db) │ │  │  │ Classifier       │ │  │  │ (SMTP/Gmail)  │ │
│  ├────────────────┤ │  │  │ (Disease Pred.)  │ │  │  └───────────────┘ │
│  │ • User Table   │ │  │  └──────────────────┘ │  │                     │
│  │ • Appointment  │ │  │                        │  │  ┌───────────────┐ │
│  │   Table        │ │  │  ┌──────────────────┐ │  │  │ ReportLab     │ │
│  └────────────────┘ │  │  │ CNN Models       │ │  │  │ (PDF Gen)     │ │
│                      │  │  │ (Brain Tumor,    │ │  │  └───────────────┘ │
│  ┌────────────────┐ │  │  │  Pneumonia,      │ │  │                     │
│  │ Training Data  │ │  │  │  Lung Cancer)    │ │  │                     │
│  │ • Training.csv │ │  │  └──────────────────┘ │  │                     │
│  │ • Testing.csv  │ │  │                        │  │                     │
│  └────────────────┘ │  │  Notebooks:            │  │                     │
│                      │  │  • brain_tumor_        │  │                     │
│  ┌────────────────┐ │  │    detection.ipynb     │  │                     │
│  │ Static Files   │ │  │  • disease-            │  │                     │
│  │ • Images       │ │  │    prediction.ipynb    │  │                     │
│  │ • PDFs         │ │  │  • lung-cancer-        │  │                     │
│  │ • Prescriptions│ │  │    prediction.ipynb    │  │                     │
│  └────────────────┘ │  │  • pneumonia-          │  │                     │
│                      │  │    detection.ipynb     │  │                     │
└──────────────────────┘  └────────────────────────┘  └─────────────────────┘
```
