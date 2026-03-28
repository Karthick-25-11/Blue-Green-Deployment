# ☕ Blue-Green Deployment using AWS (Cafe Website)

## 📌 Introduction

I built this project to understand how **zero-downtime deployments** work in real-world systems.

Instead of using a simple “Hello World” app, I created a small **cafe website** to make the concept more visual and easy to explain:

- 🟦 **Blue Environment** → Karthik’s Cafe (old version)
- 🟢 **Green Environment** → Karthick’s Cafe (updated version)

By refreshing the same Load Balancer DNS, I could clearly see traffic switching between environments along with the server IP.

---

## 🔁 What is Blue-Green Deployment?

Blue-Green Deployment is a release strategy where:

- **Blue** → Current live version  
- **Green** → New version  

Instead of updating the existing application directly, we:

1. Deploy a new version in a separate environment (Green)
2. Test it safely
3. Switch traffic from Blue → Green

👉 This ensures **no downtime** and allows quick rollback.

---

## ❓ Why is it used?

From what I understood while doing this project:

- Avoids downtime during deployments  
- Reduces risk (new version is tested before switching)  
- Instant rollback if something breaks  
- Better user experience  

---

## 🌍 Where is it used?

This strategy is commonly used in:

- Production web applications  
- E-commerce platforms  
- Banking systems  
- Any system where downtime is critical  

---

## 🛠️ Tools & Services Used

- AWS EC2  
- AWS Application Load Balancer (ALB)  
- Target Groups  
- HTML & CSS (for frontend)  

---

## 🏗️ Architecture


- ALB distributes traffic based on **weights**
- Each target group points to a different environment
  <img width="1172" height="686" alt="image" src="https://github.com/user-attachments/assets/c518ce04-86d7-4325-8ade-f667d26ebec1" />


---

## 🚀 How I Implemented This

### 1️⃣ Created Blue Environment
- Launched EC2 (Ubuntu)
- Installed Apache
- Deployed cafe website (Brown theme)

---

### 2️⃣ Created Green Environment
- Launched EC2 (Amazon Linux)
- Installed httpd
- Deployed updated cafe website (Green theme)

---

### 3️⃣ Configured Load Balancer
- Created Application Load Balancer  
- Added Listener (HTTP:80)  
- Created two target groups:
  - Blue-TG
  - Green-TG  

---

### 4️⃣ Traffic Switching

I tested different scenarios:

- **100% Blue**
- **50% Blue / 50% Green**
- **100% Green**

By refreshing the browser, I could see:
- Different UI
- Different server IP

---

### 5️⃣ Visual Enhancement

To make it clear for beginners, I added a small badge on the UI:


This made the load balancing behavior very obvious.

---

## 💥 Errors I Faced

This project taught me a lot through mistakes:

- ❌ Used wrong package (`httpd` vs `apache2`)
- ❌ Permission denied while writing HTML
- ❌ User data script issues (EOF mistake)
- ❌ Empty page due to wrong echo syntax
- ❌ Apache stopped → site not loading

👉 Debugging these issues helped me understand AWS better.

---

## 🔄 Failure Simulation & Rollback

I also tested a failure scenario:

- Stopped web server in Green  
- ALB marked it **unhealthy**  
- Users started getting errors  

Then I:

- Switched traffic back to Blue  
- Restored the application instantly  

👉 This showed how powerful rollback is in real systems.

---

## 📚 What I Learned

- How ALB routes traffic using target groups  
- Importance of health checks  
- Difference between Ubuntu & Amazon Linux  
- Real behavior of Blue-Green deployments  
- Debugging real infrastructure issues  

---

## 🎯 Conclusion

This project helped me move from **theory to practical understanding**.

Instead of just reading about Blue-Green Deployment, I:
- Built it  
- Tested it  
- Broke it  
- Fixed it  

👉 That gave me a much clearer picture of how deployments work in production.

---

