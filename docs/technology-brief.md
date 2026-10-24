# Part C: Specialized Technology

## C1. Concepts

### What is Scheduling and Optimization?

Scheduling is the process of arranging tasks or activities in a certain order based on specific rules. Optimization focuses on finding a suitable arrangement to improve efficiency and make better use of available resources.

In healthcare, scheduling can help manage patient queues and assign patients to available doctors. According to Ahmadi-Javid et al. (2017), optimization methods are commonly studied in outpatient appointment scheduling to improve healthcare operations.

### What is Weighted Priority Scheduling?

Weighted Priority Scheduling is an approach that calculates priority scores based on different factors. Each factor is given a weight according to its importance. Patients with higher calculated scores can be scheduled earlier, subject to clinical priority and queue eligibility.

For this project, the main factors are patient urgency level and waiting time. The urgency level is first reported by the patient and later verified by clinic staff. The verified urgency level is then used for the actual priority calculation.

Unlike static priority scheduling, dynamic weighted priority scheduling allows the scores to change when waiting time increases or patient information is updated.

### How the Proposed System Works

1. Patients scan a QR code to access the registration form.
2. Patients fill in their details, symptoms, pain level and self-rated urgency.
3. The system generates a queue number and displays estimated waiting time with the status "Waiting for Verification".
4. A qualified clinic staff reviews the patient information and verifies or adjusts the urgency level.
5. The system calculates the priority score using verified urgency and waiting time.
6. Patients are arranged in the eligible consultation queue based on their priority scores.
7. The system updates the queue and estimated waiting time when patient status, waiting time or doctor availability changes.

The initial waiting-time estimate is temporary because the patient's priority has not been verified. Patients who need emergency care must be assessed right away instead of waiting in the normal appointment list.


### Example of Two-Stage Weighted Priority Calculation

The proposed system uses two stages of priority calculation. The first stage uses the patient's self-rated urgency level to calculate an initial priority score. After nurse verification, the system recalculates the score using the verified urgency level and waiting time.

**Stage 1: Before Nurse Verification**

A simple proposed formula is:

Initial Priority Score = (2 × Up) + (0.1 × W)

Where:
- Up = Patient's self-rated urgency level
- W = Waiting time in minutes

Example:

| Patient | Self-Rated Urgency (Up) | Waiting Time | Initial Score |
|---------|------------------------|--------------|---------------|
| A | 3 | 10 minutes | 7 |
| B | 2 | 40 minutes | 8 |
| C | 2 | 20 minutes | 6 |

Calculation:

Patient A = (2 × 3) + (0.1 × 10) = 7

Patient B = (2 × 2) + (0.1 × 40) = 8

Patient C = (2 × 2) + (0.1 × 20) = 6

Based on the initial scores, the order is Patient B > Patient A > Patient C. However, this order is only temporary because patients will have to wait for clinic staff to verify their urgency level before the new queue order is determined.

At this stage, patients receive a queue number and temporary estimated waiting time. The system displays "Waiting for Verification" until the clinic staff reviews their urgency level. The initial scores are not used as confirmed clinical priority.

**Stage 2: After Clinic Staff Verification**

After reviewing the patient's symptoms and urgency level, the clinic staff can confirm or adjust the urgency level.

The formula is:

Verified Priority Score = (2 × Us) + (0.1 × W)

Where:
- Us = Staff-verified urgency level
- W = Waiting time in minutes

Example after verification:

| Patient | Verified Urgency (Us) | Waiting Time | Verified Score |
|---------|-----------------------|--------------|----------------|
| A | 1 | 10 minutes | 3 |
| B | 2 | 40 minutes | 8 |
| C | 4 | 20 minutes | 10 |

Calculation:

Patient A = (2 × 1) + (0.1 × 10) = 3

Patient B = (2 × 2) + (0.1 × 40) = 8

Patient C = (2 × 4) + (0.1 × 20) = 10

After staff verification, the updated order is Patient C > Patient B > Patient A.

This example shows how the priority score changes after the clinic staff verifies the patient's urgency level. The system then updates the appropriate consultation queue and estimated waiting time based on the verified priority.

In the actual system, waiting time will continue to increase and the scores can be updated dynamically.

The formulas, urgency values and weights are only examples for this conceptual study. The actual weights must be tested and evaluated before implementation. Clinical priority and emergency assessment procedures must always be followed.

## C2. Scheduling Methods and Algorithms

### 1. First Come First Served (FCFS)

FCFS is a simple scheduling method where patients are served based on their arrival time. Patients who register earlier will usually be the first to be served.

This method is easy to implement, but it does not directly consider differences in patient urgency. In this project, FCFS can be used as an alternative approach for comparison.

### 2. Static Priority Scheduling

Static Priority Scheduling arranges patients according to assigned priority levels. Patients with higher priority are normally served before patients with lower priority.

However, the priority usually stays the same unless it is manually changed. This may cause lower-priority patients to wait much longer when higher-priority patients continue to arrive.

### 3. Dynamic Weighted Priority Scheduling

Dynamic Weighted Priority Scheduling uses weighted factors to calculate patient priority scores. The scores can change based on waiting time and updated patient information.

Jiang et al. (2020) discussed a weight accumulation approach where patient priority weights increase with waiting time. This concept is relevant to the proposed system because patients' waiting times are continuously changing.

For this project, the system will recalculate priority scores after staff verification and when queue information changes.

## C3. Application to Patient Queue Management

The proposed system uses dynamic weighted priority scheduling to support patient queue management at government health clinics in Malaysia.

After registration, patients receive a queue number and a temporary estimated waiting time. The system then waits for clinic staff to verify their urgency level. Once verified, the system calculates the patient's priority score and updates the consultation queue.

If clinic staff adjust the urgency level, the system recalculates the score and estimated waiting time. The queue can also be updated when a doctor becomes unavailable.

This approach aims to support clinic staff in managing patient queues more efficiently.

### Benefits

1. **Better patient prioritisation**
   - The system considers verified priority levels and waiting time instead of depending only on arrival order.

2. **Automatic queue updates**
   - Queue information can be updated when patient status, waiting time or doctor availability changes.

3. **Improved queue monitoring**
   - Patients can check their queue status and estimated waiting time from their own device that they used to register, while clinic staff can monitor the queue through a dashboard.

### Limitations and Risks

1. **Difficulty in deciding suitable weights**
   - The system needs appropriate weights for urgency and waiting time. Incorrect weights may affect the fairness of queue arrangements.

2. **Dependence on accurate information**
   - Patients may provide incomplete or incorrect information. Therefore, qualified clinic staff must verify patient's details before it is used for confirmed scheduling.

3. **Limited doctor availability**
   - The scheduling algorithm cannot solve staff shortages. Waiting times may still increase when there are not enough available doctors.

### Comparison with FCFS

| Criteria | FCFS | Weighted Priority Scheduling |
|----------|------|------------------------------|
| Queue arrangement | Based on arrival time | Based on priority scores |
| Urgency level | Not directly considered | Considered after staff verification |
| Waiting time | Reflected through arrival order | Included in score calculation |
| Queue updates | Mainly follows arrival order | Can recalculate priority dynamically |
| Complexity | Simple | More complex |

### Reason for Choosing Weighted Priority Scheduling

Weighted Priority Scheduling is chosen because it considers patient priority and waiting time when arranging consultation queues. Compared to FCFS, it provides a more flexible approach for handling changes in patient information and waiting time.

The proposed algorithm may help clinic staff manage queues more effectively. However, its performance and fairness still need to be evaluated using dummy patient data.

