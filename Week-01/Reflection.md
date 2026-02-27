# Portfolio Task: The Dependability Strategy
**System:** Thmanyah App (Live Sports Streaming)

## 1. Required Dependability Attributes
* **Availability:** Constant access during high-traffic match kick-offs.
* **Reliability:** Continuous, freeze-free video for the full 90 minutes.
* **Safety:** Protecting user hardware from overheating and data corruption.
* **Security:** Safeguarding user accounts and protecting broadcast rights.
* **Maintainability:** Ability to fix bugs mid-match without service interruption.

---

## 2. Risk Identification
* **Hardware:** Server capacity limits being hit during major matches (e.g., Al-Hilal vs. Al-Ittihad).
* **Software:** Code bugs that cause the player to freeze or the app to crash under load.
* **Operational:** Massive spikes in concurrent users causing network congestion during "rush hour."

---

## 3. Proposed Strategy
* **Dynamic Scaling (Availability):** Automatically increase server capacity during peak traffic to prevent app crashes. 

* **Microservices (Maintainability):** Separate the video stream from other app features so the team can fix bugs without a full restart.

* **Stress Testing (Safety):** Rigorous testing of updates to ensure high-resolution streaming stays within safe device thermal limits.

* **DRM & Authentication (Security):** Implement Digital Rights Management (DRM) to protect broadcast rights from unauthorized restreaming, and enforce two-factor authentication (2FA) with encrypted sessions to safeguard user accounts.