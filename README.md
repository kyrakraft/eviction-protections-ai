# Eviction Protections Assessment Tool (EPAT)

**This tool utilizes a Large Language Model with Retrieval-Augmented Generation to identify applicable client protections for eviction cases by gathering and cross-referencing property, client, and ordinance information.**

---

## Overview

The **Eviction Protections Assessment Tool (EPAT)** is an AI-powered tool designed to assist paralegals and volunteers working with clients who have received eviction notices. EPAT intakes detailed information about the client, the property, and relevant ordinances specific to the property’s jurisdiction. Based on this data, EPAT identifies applicable protections and fills out a “3T” form, which legal staff can review and use in case responses. Additionally, EPAT provides a client-friendly summary in the client’s preferred language, explaining each protection listed on the 3T form and why it applies.

---

## Motivation

Eviction cases often move quickly, leaving clients with limited time to understand their rights. For example, the Shriver Eviction Defense Clinic works with clients facing strict 5-day deadlines for responding to eviction notices and is often overwhelmed by high demand. Determining which protections apply to each case is one of the most time-consuming steps.

EPAT’s goal is to streamline this process, reducing the time spent on each case and enabling more clients to be served daily.

**Current Status**: EPAT is in the prototyping phase. Shriver’s workflows and requirements have been defined, and the scope of EPAT’s services has been outlined.

---

## Goals

- **Primary Goal**: To identify and list all applicable client protections for eviction cases by gathering and cross-referencing property, client, and ordinance information.

---

## How It Works

EPAT uses Retrieval-Augmented Generation (RAG) to search ordinance databases for tenant protections based on specific client and property information. Protections are then mapped to a structured 3T form for legal staff to review and use in responses.

### High-Level Instructions for EPAT

1. **Collect Client Information**: Intake detailed client information, including tenancy duration, disabilities, income level, and household status.
2. **Search Ordinances**: Using RAG, EPAT cross-references client data with ordinances that apply based on the client’s location and situation.
3. **Map Protections to 3T Form**:
   - If a protection applies, check it on the 3T form.
   - If multiple protections apply, check all relevant protections, including ordinance names, clauses, and eligibility criteria.
   - For protections not listed on the 3T form but relevant to the client’s case, cite the ordinance and describe the protection in a supplementary note.
4. **Generate Client Summary**: Create a summary in the client’s preferred language, listing applicable protections and explaining the reasons each applies.

---

## Quality Standards

EPAT’s performance is evaluated using two key metrics:

- **Recall**: Measures how effectively EPAT captures all relevant protections, ensuring comprehensive coverage without omissions.
- **Precision**: Assesses EPAT’s ability to avoid unnecessary inclusions, focusing on relevant protections only to prevent overwhelming clients and legal staff.

**Summary**: EPAT aims for near-perfect recall, capturing all relevant protections, while maximizing precision without compromising recall.

---

## Training Data

EPAT currently does not rely on a static AI model, avoiding the need for frequent retraining when ordinances change. Instead, it utilizes RAG to cite ordinances in real-time.

**Challenges and Considerations**:
- **Data Privacy**: Training on real client data presents privacy risks.
- **Synthetic Data**: Creating synthetic datasets or hypothetical cases for training would require extensive resources.
- **Non-Training Alternatives**:
  - Develop a "recipe book" based on interviews with experts.
  - Use carefully crafted prompts to guide RAG’s reasoning process.

---

## Data Collection & Database Structure

- **Ordinance Scraping**: A Python script scrapes ordinances from relevant sources, with database updates occurring regularly (frequency TBD).
- **Storage**: Ordinance text is stored in a MongoDB document database with pointers for efficient access, enabling EPAT to retrieve ordinances as needed.
- **Decision Tree**: EPAT uses a decision tree to filter relevant ordinances based on geographic location and personal circumstances, ensuring protections are applied systematically.

---

## Testing & Evaluation

To assess EPAT’s accuracy, sample client stories will be tested with the AI, and legal experts will review EPAT’s recommendations to ensure accuracy and completeness.
