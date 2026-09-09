**Product Context :**

Today, analysts may need to manually review hundreds of annual reports to identify and compare the key risks disclosed by different companies.



Our goal is to build a pipeline that converts an annual report into a structured, searchable risk intelligence dataset. For this first slice, we are using the Vestas Annual Report as a representative single-report example.



**Who will be benefitted:**

* Research analysts who need to quickly understand a company's major risks.
* Asset managers who want to compare risks across companies.
* Compliance and risk teams who need traceable evidence from company disclosures.



Input -long text document (PDF), Output - Structured Data (JSON)



**Product Surface:**



The longer-term product could provide:



* Batch processing of multiple annual reports.
* An API that returns structured company-risk data.
* An interactive interface where users can search and ask questions about company risks.
* Comparisons of risks across companies and reporting years.
* Alerts when a company introduces, removes, or significantly changes a major risk.



For this first implementation, we are focusing on the single-report processing pipeline and structured JSON output, along with evaluation results.



**What We Are Optimizing For:**

The primary goal is correctness and traceability.



We want to make sure that:



* We identify the risks actually disclosed by the company.
* We avoid inventing or unnecessarily adding risks.
* Each extracted risk can be traced back to the annual report.
* The output has a consistent structure that can later be consumed by an API or UI.
* The pipeline can be evaluated objectively using a golden dataset.



Cost and processing speed are important, but they are secondary to getting the extraction quality right in this initial version.



**Basic Assumptions:**

* Annual reports are available always as PDF documents and each document contains risk related sections
* The company explicitly describes its major/principal risks.
* Source page and evidence are important for analyst confidence.



**What We Are Not Solving Yet:**



This first version does not attempt to solve the complete product.



We are intentionally deferring:



* Processing bulk documents
* Comparison of risks across different companies
* Not alerting risks, including risks that needs immediate attention
* An user interface for end-users
* Advanced user permissions and enterprise integration.
* Production deployment and infrastructure optimization.



These can be addressed after the single-report extraction and evaluation workflow is proven reliable.

