# Interview Preparation Guide

<!-- SETUP: STAR examples are personalized by running /setup based on your actual experience -->

## STAR Format

Structure answers as: **Situation** (context), **Task** (your responsibility), **Action** (what you did), **Result** (outcome).

Keep answers to 1-2 minutes. Be specific. End with what you learned or would do differently.

## Ready-Made STAR Examples

### 1. 6-DoF Model-Free Pose Estimation (technical depth / problem-solving)
**S:** TIAGo pick-and-place relied on AprilTag markers for pose estimation, which required visible fiducial markers on objects - not viable for marker-free industrial pick-and-place.
**T:** Build a model-free 6-DoF pose estimation pipeline that could replace the AprilTag front-end without markers.
**A:** Combined FoundationPose with SAM2 segmentation in ROS2 Jazzy, integrated GPU-accelerated inference (RTX 4050), and built an ADD/ATE/ARE benchmark node to validate accuracy against Gazebo ground truth.
**R:** Achieved millimeter-level pose accuracy; currently integrating the pipeline with MoveIt2 grasp planning on a UR5e arm with a Robotiq 2F-85 gripper for marker-free pick-and-place.
**Use for:** "technical deep-dive", "tell me about a challenging project"

### 2. Sensor Fusion-Based AEB System for ADAS (measurable results / safety-critical systems)
**S:** The M.Sc. research project required demonstrating a safety-critical automatic emergency braking (AEB) system under realistic driving scenarios.
**T:** Engineer a sensor-fusion pipeline combining camera and LiDAR detections to trigger reliable, interpretable braking decisions.
**A:** Fused YOLOv8 object detections with 64-channel LiDAR point clouds in CARLA 0.10; implemented a finite-state machine (Inactive-Warning-Braking) across three Euro NCAP-inspired scenario types (CCRs, CCRm, CCRb).
**R:** Achieved 98.3% collision avoidance (59/60 runs) with interpretable, explainable braking logic.
**Use for:** "tell me about a project with measurable results", "safety-critical systems experience"

### 3. Embedded Controller Upgrade at Skibbweiss (ownership / cross-domain hardware+software)
**S:** An industrial liquid filling system at Skibbweiss GmbH ran on legacy controls that needed modernization.
**T:** Design and deliver a replacement control system spanning circuit design, PCB layout, and firmware.
**A:** Designed signal-conditioning circuitry between flow meters, solenoid valves, and a Raspberry Pi Pico MCU; validated on breadboard, then produced a production-ready PCB in Altium Designer; programmed multi-channel dosing and pulse-counting logic in MicroPython.
**R:** Delivered a working production controller, taking full ownership from circuit design through to deployed firmware.
**Use for:** "ownership of a project end-to-end", "hardware/software cross-functional work"

### 4. Cognex Vision Systems at Lishtong (working under production pressure)
**S:** iPhone production lines at Lishtong needed automated optical inspection to meet strict throughput and quality targets.
**T:** Install, configure, and troubleshoot Cognex vision cameras for real-time defect and feature detection across multiple production lines.
**A:** Set up feature and defect detection tasks per line; supported calibration and on-site troubleshooting under live production conditions.
**R:** Met inspection throughput targets across multiple lines in a high-volume manufacturing environment.
**Use for:** "working under pressure/deadlines", "production/manufacturing environment experience"

### 5. Multi-Container Docker Orchestration for TIAGo Pick-and-Place (systems integration)
**S:** An autonomous pick-and-place pipeline with TIAGo needed AprilTag detection, MoveIt2 planning, and simulation to run together reliably.
**T:** Integrate these components into a single reproducible pipeline.
**A:** Orchestrated 4 containers (simulation, MoveIt2, AprilTag, workspace) across 9 Docker Compose service configurations, implementing collision-free arm planning via MoveIt2 (OMPL RRTConnect).
**R:** Delivered a full, reproducible autonomous manipulation pipeline in Gazebo.
**Use for:** "systems integration", "reproducibility/DevOps in robotics"

## Common Tough Questions

### "Why did you leave [previous company]?"
> Each move has been a deliberate step toward robotics/perception depth: Yokogawa (internship) -> Lishtong (production-line field engineering) -> relocating to Germany for the M.Sc. in Mechatronics -> Skibbweiss (Minijob applying embedded skills alongside study). Frame as intentional progression, not as leaving under a cloud.

### "You don't have [specific skill/experience]."
> Acknowledge specific gaps honestly (e.g., no formal industry robotics role yet), and bridge with concrete project evidence - the FoundationPose+SAM2 pipeline and MoveIt2 grasp-planning integration demonstrate the same underlying skills a job would require, built independently. Show willingness to learn quickly, citing the fast ramp from AprilTag-based to model-free pose estimation.

### "Where do you see yourself in 5 years?"
> Growing into a robotics engineer specializing in manipulation and perception, ideally on a research-driven team building physical AI systems - the direction the personal projects and coursework are already pointing toward.

### "What's your biggest weakness?"
> [TO BE FILLED - this needs a genuine, personal answer with a concrete mitigation strategy. Discuss with the candidate before an actual interview; do not fabricate one.]

### "Why this company specifically?"
> Customize per company. Must reference: specific projects, company values, market position, or team structure. Never give a generic answer.

## Questions You Should Ask Interviewers

### About the Role
- "What does a typical week look like in this role?"
- "What would success look like in the first 6 months?"
- "What's the biggest challenge the team is facing right now?"

### About the Team
- "How big is the team, and how do you divide work?"
- "What does the development/project lifecycle look like, from idea to production?"
- "How do you onboard new team members?"

### About Tech & Growth
- "What's your current tech stack for [relevant area]?"
- "Is there room to grow into more architectural or strategic decisions?"
- "How does the team stay current with new tools and methods?"

### About Culture (use these to prevent disappointment)
- "How would you describe the team culture?"
- "What does professional development look like here?"
- "Is there flexibility for remote/hybrid work?"
- "What's the balance between development/new projects and maintenance work?"
- "How would you describe the leadership style in this team?"
- "What do people who thrive here have in common?"

## Phone/Video Interview Tips
- Have STAR examples written out (use this file)
- Keep a glass of water nearby
- Smile when speaking (it changes your tone)
- Ask for clarification if a question is vague
- It's OK to take 5 seconds to think before answering
- End with: "Is there anything else you'd like to know about my background?"

## After the Application (Best Practice)

### Follow-Up Etiquette
- **Don't call to "stand out"** or to learn more about the role post-submission - this risks a negative impression
- If the employer specified a timeline, respect it and wait
- If no timeline was given and significant time has passed (2+ weeks), a brief call to ask about status is acceptable
- If you have genuinely new, relevant information to share, a short follow-up is fine

### Thank-You Notes
- When you receive any update (interview invitation, rejection, or status update), send a brief thank-you message
- Express appreciation for their time and the process
- Keep it short (2-3 sentences)

## Roleplay Guidelines
When the user asks for interview practice:
1. Ask which role/company to simulate
2. Start with easy warm-up questions ("Tell me about yourself")
3. Progress to role-specific technical questions
4. Include 1-2 behavioral questions using the competencies from the job posting
5. End with a tough question or curveball
6. After each answer, give brief feedback: what worked, what to sharpen
7. Suggest which STAR example would work best for each question
