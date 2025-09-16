# Healthcare Analytics to Elevate Patient Care #

Mayo Clinic, founded in 1889, stands as one of the world’s leading nonprofit healthcare providers with a rich legacy of excellence. 
Its enduring success stems from an unwavering commitment to patient-centered care, powered by advanced healthcare analytics.

By harnessing vast volumes of patient data, Mayo Clinic has unlocked critical insights to strengthen:

    Clinical decision support

    Patient risk stratification

    Resource optimization

    Patient experience strategies

Through this data-driven approach, Mayo Clinic has built a model of care designed to:

    Improve patient outcomes

    Enhance operational efficiency

    Drive continuous innovation in medical treatments and therapies

At its core, Mayo Clinic’s story is one of leveraging analytics not just to inform decisions, 
but to shape a future where medicine remains deeply patient-centric while advancing the boundaries of healthcare.

# About Dataset #

The hospital patient dataset provides a comprehensive overview of patient information, encompassing biographical details.
| Column Name           | Data Type        | Description                                  |
|-----------------------|------------------|----------------------------------------------|
| date                  | date             | Date of patient visit or record              |
| patient_id            | Integer/String   | Unique identifier for each patient           |
| patient_gender        | String           | Gender of the patient                        |
| patient_age           | Integer          | Age of the patient                           |
| patient_race          | String           | Patient's race or ethnicity                  |
| patient_sat_score     | Integer          | Patient's Satisfaction score                 |
| patient_first_initial | String           | First initial of the patient's name          |
| patient_last_name     | String           | Last name of the patient                     |
| patient_admin_flag    | Boolean          | Flag indicating administrative status        |
| patient_waittime      | Integer          | Wait time for the patient                    |
| department_referral   | String           | Department or source of referral             |
| time_slot             | String           | Time slot or appointment time for the patient|

## Approach ##
### Step 1: Identify the stakeholder ###
| Stakeholder              | Needs & Interests                                      | Challenges                                           |
|--------------------------|--------------------------------------------------------|------------------------------------------------------|
| Physicians/Providers     | - Accurate medical histories<br>- Treatment outcome data<br>- Medication response tracking<br>- Patient satisfaction info<br>- Clinical research findings | - Reducing medical errors<br>- Managing patient loads<br>- Ensuring adherence to best practices<br>- Providing personalized care |
| Patients                 | - Quality care<br>- Clear communication<br>- Improved outcomes<br>- Personalized treatments                        | - Timely access<br>- Understanding treatment plans<br>- Navigating complex systems    |
| Administrators           | - Resource usage stats<br>- Visit volumes<br>- Satisfaction metrics<br>- Operational efficiency                      | - Balancing workloads<br>- Optimizing processes<br>- Regulatory compliance           |
| Researchers/Analysts     | - Clinical data<br>- Outcome and satisfaction metrics                              | - Data integrity<br>- Research participation<br>- Translating findings to practice   |
### Step 2: Design empathy map ### 
https://www.yeschat.ai/
| Quadrant        | Color & Icon                     | Key Thoughts & Content                                                                                     |
|-----------------|---------------------------------|------------------------------------------------------------------------------------------------------------|
| **Think & Feel** | Calm Blue 💭❤️                  | - "How can I provide the best care with limited resources?"<br>- "Am I keeping up with new research?"<br>- Feels responsible and proud but stressed and fatigued<br>- Frustrated by systemic barriers  |
| **See & Hear**  | Teal/Green 👀👂                  | - Sees overcrowded waiting rooms and constant EHR alerts<br>- Notices breakthroughs and setbacks in medical news<br>- Hears patients’ fears, hopes, and frustrations<br>- Hears administrators focus on compliance and costs |
| **Say & Do**    | Purple 🗨️✍️                    | - Says: "I wish I had more time with patients" / "We need better tools"<br>- Reads medical journals and participates in continuing education<br>- Consults colleagues and advocates for patients<br>- Documents care thoroughly in EHR  |
| **Pains & Goals**| Warm Orange ⚡🎯               | - Pains: Administrative burden, burnout, emotional toll, pressure from technology<br>- Goals: Deliver evidence-based care, maintain balance, stay current with research, drive systemic improvement  |

### Step 3: Identify KPIs ### 
| KPI                       | Formula                                         | Description                                                  |
|---------------------------|------------------------------------------------|--------------------------------------------------------------|
| Monthly Patient Visits     | Total patient visits in a month                 | Tracks patient volume monthly to support resource and revenue planning. |
| Patient Visits by Time     | Visits in AM or PM                              | Measures morning vs. afternoon visit distribution for staffing optimization. |
| Patient Satisfaction Score | Total satisfaction score / Number of surveyed patients | Evaluates overall patient satisfaction, impacting reputation and loyalty. |
| Gender-wise Patient Breakdown | (Male or Female patients / Total patients) * 100 | Shows gender distribution, aiding tailored care and health disparity insights. |
| Readmission Rate           | Readmissions within 30 days / Discharged patients | Indicates quality of care and issues in patient transitions. |
| Clinic Utilization         | Patient visits / Total available appointments  | Measures clinic resource usage efficiency and access to care. |

### Step 4: Understand goals and Objectives of User ### 
| Section    | Points                                                                                                                        |
|------------|-------------------------------------------------------------------------------------------------------------------------------|
| **Objective** | - Analyze patient data and healthcare operations. <br> - Improve patient outcomes and quality of care. <br> - Optimize resource utilization. <br> - Understand patient satisfaction, visit patterns, readmission rates, and clinical performance. <br> - Identify areas for improvement and develop strategies to boost satisfaction, care delivery, and efficiency. |
| **Goal**     | - Increase patient satisfaction by enhancing communication, care coordination, and patient experience. <br> - Analyze monthly visit patterns to optimize staffing and resource allocation. <br> - Reduce readmissions through better discharge planning, care transitions, and follow-up. <br> - Improve clinic utilization by streamlining scheduling and minimizing no-shows to maximize access and resource use. |

### Step 5: Ask Business Questions ### 

     1. What is the monthly breakdown of patient visits?

     2. How do patient visits compare between AM and PM time slots?

     3. How are patients distributed among various departments based on referrals?

     4. What is the gender breakdown of patients?

     5. What is the average satisfaction score by age group and gender?

     6. How do patient visits vary by age group?

     7. What is the count of patient visits by category (walk-ins vs referrals)?

     8. How do patient visits differ by day type (weekends vs weekdays)?

### How to run ### 

    Run the .ipynb
    
### Insights ### 

    >> In August, there was a peak in patient visits for the year, with 1024 registered patients, 
    indicating a possible seasonal trend or event-driven demand in healthcare services during this month. 
    In contrast, January saw the lowest with 431 visits, suggesting varying healthcare utilization patterns throughout the year.

    >> The distribution of patient visits between AM and PM is almost equal, with 4632 visits in the morning and 4584 in the afternoon, 
    demonstrating a steady and balanced demand for healthcare services throughout the day.

    >> A significant number of patients (5400) were not referred to any specific department, 
    illustrating a significant volume of general or non-specialized healthcare needs. 
    Among specialized referrals, 
    General Practice and Orthopedics were the most frequented, pointing to prevalent general health and musculoskeletal issues among the patient population.

    >> There is a slight female predominance in patient visits, with females making up 51% and males 49%, 
    reflecting a marginally higher healthcare utilization by women in the observed patient population.

    >> The highest satisfaction scores are seen in the 21-30 age group, particularly among females, 
    suggesting higher satisfaction with healthcare services in younger adults. 
    Conversely, other age groups such as 31-40, 11-20, and those over 50 reported lower satisfaction, indicating potential areas for service improvement.

    >> The "over 50" age group had the highest number of visits, underscoring a greater healthcare requirement in this demographic. 
    Conversely, the 0-10 age group had the fewest visits, highlighting lower healthcare engagement or need among younger children.


