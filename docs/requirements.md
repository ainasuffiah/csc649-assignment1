# Part B: Requirements

## Functional Requirements (what the system must DO)

- **FR1:** The system shall allow patients to check their queue number and status.
- **FR2:** The system shall display patients' estimated waiting time.
- **FR3:** The system shall calculate patient priority scores based on urgency level and waiting time using weighted priority scheduling.
- **FR4:** The system shall assign patients to an available consultation queue based on their priority scores.
- **FR5:** The system shall update patient queue assignments when a doctor becomes unavailable.
- **FR6:** The system shall allow patients to access the registration form through a QR code.
- **FR7:** The system shall allow patients to submit their registration details.
- **FR8:** The system shall generate a unique queue number after successful registration.
- **FR9:** The system shall allow clinic staff to update patient status.
- **FR10:** The system shall allow clinic staff to update doctor availability.

## Non-Functional Requirements (how the system must PERFORM)

- **NFR1 (Security):** The system shall allow only authorised clinic staff to access the queue management dashboard.
- **NFR2 (Performance):** The system shall display queue information within 5 seconds when tested under normal conditions. 
- **NFR3 (Usability):** Patients shall be able to complete registration in no more than 5 steps after scanning the QR code.
- **NFR4 (Reliability):** The system shall keep registered queue records after the webpage is refreshed.
