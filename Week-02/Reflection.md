# Portfolio Task: Build Your Proof
**System:** Uber Rider App 

## 1. Define the Profile
* **The User:** Everyday commuters, travelers, and residents who use the app in time sensitive or high stress situations (e.g., catching a flight or heading home late at night).
* **The Pattern:** Usage is **Intermittent but Critical**. A rider may only trigger a "Demand" twice a day, but that specific interaction must be 100% successful. The system handles traffic where the user's focus is entirely on a 60-second window: from pressing "Request" to receiving a driver confirmation.

## 2. Choose the Metric: POFOD (Probability of Failure on Demand)
* **Selection:** **POFOD**
* **Justification:** While Uber as a whole cares about "Uptime" (Availability), the individual rider's trust is built on the success of a single button press. If a rider is standing in the rain and hits "Request," they don't care if the system was up all morning; they care if it fails *right now*. POFOD measures the likelihood that the system will fail to satisfy that specific request. High POFOD leads to a loss of trust, whereas a low POFOD proves the system is dependable in the "eyes of the user".



## 3. Propose Strategy: Fault Tolerance via Timeouts & Redundancy
* **Decision:** I will implement **Commandment #7 (Include Timeouts)** as the primary code-level defense, supported by **Hardware Redundancy**.
* **Description:** Mobile networks are inherently unreliable. To prevent a technical **Fault** (lost signal) from becoming a visible **Failure** (app freeze), the app will "assume external calls will hang." 
* **Architectural Decision:** I will set a 5-second timeout on the matching request. If the primary server fails to respond, the system will automatically trigger a retry on a **Redundant** server cluster. This ensures the "Infection" (Error) is handled at the **Runtime Phase** , providing a seamless experience for the rider.



---

## 4. Justification

In engineering the Uber Rider experience, we must manage the **Mechanics of Failure** to preserve user trust. According to the **Chain of Failure** , a "Fault" in a local network tower or a data center can "infect" the user’s session, creating an "Error." If our architecture is not defensive, this results in a "Failure"—a rider stranded without a ride. 

Because the rider's interaction is a discrete "Demand," we prioritize **POFOD**. Unlike a streaming service where a minor glitch might be ignored (ROCOF), a failed ride request is a total service deviation. By focusing on POFOD, we align our engineering goals with the user's primary need: certainty.

To achieve a low POFOD, we move to the **Third Line of Defense: Fault Tolerance** . We acknowledge that we cannot control the "wear and tear" of global hardware, so we use **Redundancy**. By running the matching logic across identical server copies, we ensure that if one node fails, the rider's demand is caught by another. 

Furthermore, we apply **Commandment #7** from the "8 Commandments of Reliability" . By building the app to "Include Timeouts," we ensure that the software remains responsive. Instead of a silent failure or a "magic number" crash, the app acknowledges the delay and attempts a recovery state. We accept that achieving 100% reliability is "infinitely expensive", but by strategically applying **Redundancy** and **Defensive Programming**, we create a system that is robust enough to be considered "Proven" in the eyes of the rider.

---

## 5. Architectural Diagram
![Diagram](https://github.com/user-attachments/assets/db63b5c2-ce54-495c-9470-f16065b243a7)

