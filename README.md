# Urban Waste Clogging & Flood Risk Early Warning System (UWCF-EWS)

**Module:** PROG101 - Programming Logic and Design  
**Institution:** Limkokwing University of Creative Technology, Sierra Leone  
**Student:** Joseph Calvin Turay (ID: 905005832)  
**Class:** B.S.E.M. 1101 | Semester 1, Year 1  
**Lecturer:** Mr. Elijah Fullah  

---

##  Project Overview
Freetown, Sierra Leone, faces extreme seasonal flash flooding exacerbated by solid waste accumulation in urban drainage channels. The **UWCF-EWS** is a non-code logical decision support tool designed to evaluate real-time rainfall intensity (mm/hr) and drainage blockage percentages (0–100%) to calculate a composite risk score and issue automated alert levels (`LOW`, `MODERATE`, `HIGH`, `CRITICAL`).

---

##  Sustainable Development Goals (SDGs)
* **SDG 11: Sustainable Cities and Communities (Target 11.5):** Reduces localized flood risks and enhances disaster resilience in high-vulnerability informal settlements across Freetown (e.g., Kroo Bay, Susan's Bay, Kulakaray).

---

##  Logic & Formula
$$\text{Risk Score} = (\text{Rainfall} \times 0.6) + (\text{Blockage} \times 0.4)$$

| Risk Score Range | Alert Tier | Action Directive |
| :--- | :--- | :--- |
| **0 – 19.9** | **LOW** | Normal routine maintenance required. |
| **20.0 – 44.9** | **MODERATE** | Schedule community drain clearance. |
| **45.0 – 69.9** | **HIGH** | Dispatch cleanup teams immediately! |
| **70.0 +** | **CRITICAL** | Trigger emergency evacuation & flood response! |

---

##  Pseudocode

```text
START

    String community
    Real rain, blockage, risk
    String level, choice
    Boolean run = TRUE

    WHILE run == TRUE DO
        
        DISPLAY "Enter community name:"
        INPUT community

        DISPLAY "Enter rainfall in mm/hr:"
        INPUT rain

        DISPLAY "Enter drain blockage percentage (0-100):"
        INPUT blockage

        IF rain < 0 OR blockage < 0 OR blockage > 100 THEN
            DISPLAY "Error: Invalid numbers entered."
        ELSE
            risk = (rain * 0.6) + (blockage * 0.4)

            IF risk < 20 THEN
                level = "LOW"
            ELSE IF risk < 45 THEN
                level = "MODERATE"
            ELSE IF risk < 70 THEN
                level = "HIGH"
            ELSE
                level = "CRITICAL"
            END IF

            DISPLAY "-----------------------------------"
            DISPLAY "Community: " + community
            DISPLAY "Risk Score: " + risk
            DISPLAY "Alert Level: " + level
            DISPLAY "-----------------------------------"
        END IF

        DISPLAY "Analyze another community? (YES/NO):"
        INPUT choice
        
        IF choice == "NO" OR choice == "no" OR choice == "No" OR choice == "N" OR choice == "n" THEN
            run = FALSE
        END IF

    END WHILE

    DISPLAY "System closed."

END
