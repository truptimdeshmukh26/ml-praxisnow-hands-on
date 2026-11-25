# Data: `praxisnow_appointments.csv`

**Synthetic** data made for this course: 6,228 appointments of 2,300 made-up patients at a fictional group of practices, 5 January – 30 October 2026. No real patients and no real company. One row = one booked appointment that was **not cancelled in advance**.

| column | type | meaning | known at booking? |
|---|---|---|---|
| `appointment_id` | ID | one per appointment | – |
| `patient_id` | ID | a patient can have several appointments | – |
| `booked_at` | date | the day the appointment was booked | ✅ |
| `appointment_at` | date + time | when the appointment takes place (weekdays, 08:00–18:00) | ✅ |
| `clinic_city` | category | Berlin, Hamburg, Munich, Cologne, Leipzig | ✅ |
| `specialty` | category | general_practice, dermatology, dentistry, physiotherapy, orthopaedics | ✅ |
| `booking_channel` | category | app, website, phone | ✅ |
| `age` | number | patient's age in years (18–92) | ✅ |
| `insurance` | category | `public` or `private` health insurance | ✅ |
| `distance_km` | number | distance from home to the practice; **empty** = address not shared (13%) | ✅ |
| `sms_opt_in` | 0/1 | patient agreed to SMS reminders (64%) | ✅ |
| `prior_appointments` | count | the patient's appointments whose date was **before the booking day** of this one (only those are over and known) | ✅ |
| `prior_no_shows` | count | how many of those `prior_appointments` were no-shows | ✅ |
| `reminder_reply` | category | reply to the SMS sent **24 h before**: `confirmed` / `no_reply`; empty = no SMS (patient didn't opt in) | ❌ (24 h before) |
| `wait_time_min` | number | minutes in the waiting room; **empty for every no-show** | ❌ (after the appointment) |
| **`no_show`** | **0/1** | **target**: 1 = the patient didn't come and didn't cancel | ❌ |

**Two simplifications to know:**
- The data starts on 5 January 2026, so the history columns only count appointments from that day on. Early appointments therefore show little history (one reason the test months have more history on average than the training months).
- The table only has appointments that were **not cancelled in advance**. At booking time you can't know that yet; a real system would also score bookings that later get cancelled.

**How the history columns are built:** for each appointment, only the same patient's appointments that took place **before the day it was booked** are counted. An earlier booking that was still in the future at that moment is not counted, even if the patient later missed it. The generator checks this for every row.

**Facts to sanity-check your work:** 21.0% no-shows overall · train (appointments Jan–Jul) 4,354 rows, 21.3% · test (appointments Aug–Oct) 1,874 rows, 20.3%.
