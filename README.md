# Jeremiah Alao — Engineering Portfolio

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live%20Site-blue?style=flat&logo=github)](https://youniquestar.github.io)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat&logo=linkedin)](https://www.linkedin.com/in/jeremiah-alao/)
[![GitHub](https://img.shields.io/badge/GitHub-youniquestar-181717?style=flat&logo=github)](https://github.com/youniquestar)

Personal engineering portfolio website for **Jeremiah Alao**, showcasing multidisciplinary expertise across **Robotics & Motion Control**, **Bare-Metal Embedded Systems**, **Computer Vision & Sensor Fusion**, and **Production AI/ML Engineering**.

Hosted with GitHub Pages at [youniquestar.github.io](https://youniquestar.github.io).

---

## 🚀 Featured Engineering Projects

| Order | Project | Focus Area | Technologies | GitHub |
|---|---|---|---|---|
| **01** | [**Astari Selah — 5-DOF Robotic Arm**](_projects/astari-selah/index.md) | Robotics & Kinematics | ROS 2 Humble, ESP32, FreeRTOS, FreeCAD, URDF/Xacro, Gazebo | [youniquestar/astari-selah](https://github.com/youniquestar/astari-selah) |
| **02** | [**Pulse AI — Predictive Maintenance Engine**](_projects/pulse-ai/index.md) | Machine Learning & Telemetry | Python, Scikit-learn, FastAPI, Pandas, Anomaly Detection | [youniquestar/pulse-ai](https://github.com/youniquestar/pulse-ai) |
| **03** | [**AI Health Partner — Clinical Triage**](_projects/ai-health-partner/index.md) | Conversational AI & NLP | Python, State Machine Architecture, Clinical NLP, REST API | [youniquestar/ai_health_partner](https://github.com/youniquestar/ai_health_partner) |
| **04** | [**ESP32 Wireless Robotics Controller**](_projects/esp32-wireless-controller/index.md) | Embedded Wireless Systems | ESP32, ESP-NOW (&lt;5ms latency), C++, FreeRTOS, PWM | [youniquestar/esp32-wireless-robotics-controller](https://github.com/youniquestar/esp32-wireless-robotics-controller) |
| **05** | [**Autonomous Human-Following Robot**](_projects/human-following-robot/index.md) | Autonomous Mobile Robots | Arduino, Ultrasonic HC-SR04, Dual IR Tracking, L298N | [youniquestar/arduino-human-following-robot](https://github.com/youniquestar/arduino-human-following-robot) |
| **06** | [**Smart Irrigation System**](_projects/smart-irrigation/index.md) | IoT & Microclimate Sensing | Arduino, Soil Moisture, DHT11, Relays, Swept Servo | [youniquestar/arduino-smart-irrigation-system](https://github.com/youniquestar/arduino-smart-irrigation-system) |
| **07** | [**RFID Barrier Gate Access Control**](_projects/rfid-barrier-gate/index.md) | Physical Security & Hardware | Arduino Nano, MFRC522 RFID, SPI, MG90S Servo | [youniquestar/arduino-rfid-barrier-gate](https://github.com/youniquestar/arduino-rfid-barrier-gate) |
| **08** | [**Smart Assistive Walking Stick**](_projects/smart-walking-stick/index.md) | Assistive Tech & Haptics | Arduino, Ultrasonic Ranging, Dual-Tone Audio, Haptic Motor | [youniquestar/arduino-smart-walking-stick](https://github.com/youniquestar/arduino-smart-walking-stick) |
| **09** | [**LASUSTECH FAQ Chatbot**](_projects/school-faq-chatbot/index.md) | NLP & Pattern Matching | Python, Regex Pattern Matching, Academic Data Simulator | [youniquestar/school_faq_chatbot](https://github.com/youniquestar/school_faq_chatbot) |

---

## 🛠️ Technical Stack & Skills

- **Robotics & Simulation**: ROS 2 Humble, Forward & Inverse Kinematics (DH parameters), URDF / Xacro, Gazebo, RViz2
- **Embedded & Microcontrollers**: ESP32 (ESP-NOW, FreeRTOS), Arduino (Uno, Nano, Mega), SPI, I2C, UART, PWM
- **AI & Machine Learning**: Python, Scikit-learn, NumPy, Pandas, FastAPI, Anomaly Detection, State Machines
- **CAD & Prototyping**: Autodesk Fusion 360, FreeCAD PartDesign, 3D Printing (FDM), Rapid Breadboarding
- **Software & Systems**: Linux (Ubuntu), Git & GitHub, Docker, Bash scripting

---

## 📂 Repository Structure

```
Portfolio/
├── _config.yml               # Jekyll site configuration & biography data
├── _includes/
│   ├── hero.html             # Hero section with avatar and socials
│   ├── projects.html         # Featured project cards grid
│   ├── skills.html           # Technical competencies grid
│   ├── contact.html          # Contact form & channels
│   ├── navbar.html           # Responsive navigation bar
│   └── footer.html           # Footer with links and license attribution
├── _layouts/
│   ├── wrapper.html          # Main HTML5 semantic layout
│   └── post.html             # Project detail page template
├── _projects/                # Project markdown pages and asset thumbnails
│   ├── astari-selah/
│   ├── pulse-ai/
│   ├── ai-health-partner/
│   ├── esp32-wireless-controller/
│   ├── human-following-robot/
│   ├── smart-irrigation/
│   ├── rfid-barrier-gate/
│   ├── smart-walking-stick/
│   └── school-faq-chatbot/
├── assets/
│   ├── images/profile-image/ # Headshot
│   └── js/                   # Interactive scripts (mobile menu, etc.)
├── css/
│   ├── styles.css            # Custom responsive CSS design system
│   └── syntax.css            # Dark mode code block syntax highlighting
└── index.html                # Portfolio landing page
```

---

## 💻 Local Preview & Development

To preview locally using Jekyll:

```bash
# Clone the repository
git clone https://github.com/youniquestar/youniquestar.github.io.git Portfolio
cd Portfolio

# Install dependencies
bundle install

# Run the local server
bundle exec jekyll serve
```

The site will be available at `http://localhost:4000`.

---

## 📄 License & Attribution

- Site content and project write-ups © Jeremiah Alao.
- Base layout adapted from the open-source Free-To-Engineer template by lowinertia.com ([CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)).
