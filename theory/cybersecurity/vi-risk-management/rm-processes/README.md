# RM processes

## RISK MANAGEMENT PROCESSES

\
Risk management is a process for identifying, assessing, and mitigating vulnerabilities and threats to the essential functions that a business must perform to serve its customers. You can think of this process as being performed over five phases:

<figure><img src="../../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

##

Based on NIST SP 800-30, the risk management process entails four steps:

1. Frame risk: First, we must establish the context within which all risk activities occur.
2. Assess risk: We must identify, analyse, and evaluate potential risks and their likelihood and impact. This step is crucial to help decide on a proper response later.
3. Respond to risk: We need to take the steps necessary to mitigate the likelihood or impact of the risk. The response depends on many factors, and we will cover them separately.
4. Monitor risk: Finally, we continue tracking and evaluating the effectiveness of risk responses, identifying new risks, and ensuring that our risk management activities are effective. Monitoring is an ongoing process, as many criteria might change over time.

## Step 1: Risk Identification

The first step in the risk management process is to identify all the events that can negatively (risk) or positively (opportunity) affect the objectives of the project:

* Project milestones
* Financial trajectory of the project
* Project scope

These events can be listed in the risk matrix and later captured in the risk register.

A risk (or opportunity) is characterized by its description, causes and consequences, qualitative assessment, quantitative assessment and mitigation plan. It can also be characterized by who is responsible for its action. Each of these characteristics are necessary for a risk (or opportunity) to be valid.

In order to be managed effectively, the Risks and Opportunities (R\&O) identified must be as precise and specific as possible. The title of the risk or opportunity must be succinct, self-explanatory and clearly defined.&#x20;

All members of the project can and should identify R\&O, and the content of these is the responsibility of the Risk (or Opportunity) Owners. Risk Managers are responsible for ensuring that a formal process for identifying risks and developing response plans are conducted through exchanges with risk owners. We will explain each of these roles in further detail in our next article on [Risk Management Team Roles](https://www.migso-pcubed.com/blog/risk-management/risk-management-team-roles/).

Below are examples of tools to help identify R\&O:

* Analysis of existing documentation
* Interviews with experts
* Conducting brainstorming meetings
* Using the approaches of standard methodologies – such as Failure Modes, Effects and Criticality Analysis (FMECA), cause trees, etc.
* Considering the lessons learned from R\&Os encountered in previous projects&#x20;
* Using pre-established checklists or questionnaires covering the different areas of the project (Risk Breakdown Structure or RBS).

### RISK TYPES

The initial step in the risk management process is to identify the risks that the business is exposed to in its operating environment.

There are many different types of risks:

* Legal risks
* Environmental risks
* Market risks
* Regulatory risks etc.

#### External <a href="#c96dc336-fb75-4eb9-8299-61e4084217ef" id="c96dc336-fb75-4eb9-8299-61e4084217ef"></a>

#### Internal <a href="#id-0a531cfe-aa0c-48e7-bbc3-0817ccc99ba2" id="id-0a531cfe-aa0c-48e7-bbc3-0817ccc99ba2"></a>

Internal risks come from assets and workflows that are owned and managed by your organization. When reviewing internal risks, it is important to remember that these can be classed as malicious or accidental (non-malicious). Internal threats can include contractors who were granted temporary access.

#### Multiparty <a href="#dda8fe87-d030-403a-a531-b9218e74d6f1" id="dda8fe87-d030-403a-a531-b9218e74d6f1"></a>

Multiparty risk is where an adverse event impacts multiple organizations. Multiparty risk usually arises from supplier relationships. If a critical event disrupts a supplier or customer, then your own organization will suffer. These are often described as ripple impacts. For example, if one of your top five customers goes out of business because of a data breach, your company will lose substantial revenue. Organizations in these supply chain relationships have an interest in promoting cybersecurity awareness and capability throughout the chain.

As an illustration of how risk assessments can change in view of multiparty relationship, consider a company that makes wireless adapters, originally for use with laptops. In the original usage, the security of the firmware upgrade process is important, but it has no impact on life or safety. The company, however, earns a new contract to supply the adapters to provide connectivity for in-vehicle electronics systems. Unknown to the company, a weakness in the design of the in-vehicle system allows an adversary to use compromised wireless adapter firmware to affect the car's control systems. The integrity of the upgrade process now has an impact on safety, and is much higher risk.

#### Intellectual Property (IP) Theft <a href="#a51a750d-3ca0-4d2a-8d43-6f61edce618f" id="a51a750d-3ca0-4d2a-8d43-6f61edce618f"></a>

Intellectual property (IP) is data of commercial value that is owned by the organization. This can mean copyrighted material for retail (software, written work, video, and music) and product designs and patents. If IP data is exfiltrated it will lose much of its commercial value. Losses can be very difficult to recover in territories where there are not strong legal protections.

#### Software Compliance/Licensing <a href="#d616712d-30e3-43a4-9024-67553e6d12db" id="d616712d-30e3-43a4-9024-67553e6d12db"></a>

Breaking the terms of the end user licensing agreement (EULA) that imposes conditions on installation of the software can expose the computer owner to substantial fines. License issues are most likely to arise from shadow IT, where users install software without change control approval. Network inventory management suites can report software installations on each host and correlate those with the number of license seats purchased. Licensing models can also be complex, especially where virtualization and the cloud are concerned. It is important to train the administrative staff on the specific license terms for each product.

#### Legacy Systems <a href="#id-9b7136fe-99d3-42f7-90af-26684d961f12" id="id-9b7136fe-99d3-42f7-90af-26684d961f12"></a>

Legacy systems are a source of risk because they no longer receive security updates and because the expertise to maintain and troubleshoot them is a scarce resource.

\
\


## Step 2: Analyze the Risk

Once a risk has been identified it needs to be analyzed. The scope of the risk must be determined. It is also important to understand the link between the risk and different factors within the organization. To determine the severity and seriousness of the risk it is necessary to see how many business functions the risk affects. There are risks that can bring the whole business to a standstill if actualized, while there are risks that will only be minor inconveniences in the analysis.

In a manual risk management environment, this analysis must be done manually.When a risk management solution is implemented one of the most important basic steps is to map risks to different documents, policies, procedures, and business processes. This means that the system will already have a mapped [risk management framework](https://www.360factors.com/blog/risk-management-framework/) that will evaluate risks and let you know the far-reaching effects of each risk.



#### QUANTITATIVE RISK ASSESSMENT

There are quantitative and qualitative methods of performing risk analysis to evaluate likelihood and impact.

Quantitative risk assessment aims to assign concrete values to each risk factor.

* Single Loss Expectancy (SLE)—the amount that would be lost in a single occurrence of the risk factor. This is determined by multiplying the value of the asset by an Exposure Factor (EF). EF is the percentage of the asset value that would be lost.
* Annualized Loss Expectancy (ALE)—the amount that would be lost over the course of a year. This is determined by multiplying the SLE by the Annualized Rate of Occurrence (ARO).

It is important to realize that the value of an asset does not refer solely to its material value. The two principal additional considerations are direct costs associated with the asset being compromised (downtime) and consequent costs to intangible assets, such as the company's reputation. For example, a server may have a material cost of a few hundred dollars. If the server were stolen, the costs incurred from not being able to do business until it can be recovered or replaced could run to thousands of dollars. In addition, that period of interruption where orders cannot be taken or go unfulfilled leads customers to look at alternative suppliers, resulting in perhaps more thousands of lost sales and goodwill.

The problem with quantitative risk assessment is that the process of determining and assigning these values is complex and time consuming. The accuracy of the values assigned is also difficult to determine without historical data (often, it has to be based on subjective guesswork). However, over time and with experience, this approach can yield a detailed and sophisticated description of assets and risks and provide a sound basis for justifying and prioritizing security expenditure.

#### QUALITATIVE RISK ASSESSMENT

Qualitative risk assessment avoids the complexity of the quantitative approach and is focused on identifying significant risk factors. The qualitative approach seeks out people's opinions of which risk factors are significant. Assets and risks may be placed in simple categories. For example, assets could be categorized as Irreplaceable, High Value, Medium Value, and Low Value; risks could be categorized as one-off or recurring and as Critical, High, Medium, and Low probability.

Another simple approach is the heat map or "Traffic Light" impact matrix. For each risk, a simple Red, Yellow, or Green indicator can be put into each column to represent the severity of the risk, its likelihood, cost of controls, and so on. This approach is simplistic but does give an immediate impression of where efforts should be concentrated to improve security.



FIPS 199 ([nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.199.pdf](https://wmx-api-production.s3.amazonaws.com/courses/5731/supplementary/NIST.FIPS.199.pdf)) discusses how to apply security categorizations (SC) to information systems based on the impact that a breach of confidentiality, integrity, or availability would have on the organization as a whole. Potential impacts can be classified as:

* Low—minor damage or loss to an asset or loss of performance (though essential functions remain operational).
* Moderate—significant damage or loss to assets or performance.
* High—major damage or loss or the inability to perform one or more essential functions.

#### Qualitative Assessment

The Risk Owner and the Risk Manager will rank and prioritize each identified risk and opportunity by occurrence probability and impact severity, according to the project’s criticality scales.

**Evaluating occurrence probability (P):**

This is determined preferably based on experience, the progress of the project, or else by speaking to a risk expert, and is on a scale of 1 to 99%.

For example, suppose the risk that: “the inability of supplier X to conduct studies on a modification Y by the end of 2025” is 50% probable. This could be determined from feedback and analysis of the supplier’s workload.

**Evaluating impacts severity (I):**

To assess the overall impact, it is necessary to estimate the severity of each of the impacts defined at the project level. A scale is used to classify the different impacts and their severities. This ensures that the assessment of the risk and opportunity is standardized and reliable.

The criticality level of a risk or opportunity is obtained by the equation: **Criticality = P x I**

The purpose of the qualitative assessment is to ensure that the risk management team prioritizes the response on critical items first.

## Step 3: Prioritizing the Risks

Now, it's time to prioritize the identified risks based on how critical they are. This is done by looking at the likelihood of each risk happening and the impact it might create on the business, and assigning them an appropriate rank.&#x20;

So, a risk that would cause a little inconvenience but not disrupt business operations much is given a low rank while one that can bring the entire business to a standstill would be ranked the highest.&#x20;

This step gives you a holistic view of your organization's risk exposure. More importantly, it helps you identify where you should focus more of your team's time and resources. Based on this ranking information, you can also create workable solutions to manage each risk so that your operations are not significantly affected during the risk treatment phase.&#x20;

## 4. Treat the risks

With a prioritized list of risks in place, the next step is to evaluate the options available to treat, or respond to, the risks and decide which approach to apply in each case. Potential risk treatment actions including the following:

* Risk acceptance. If a risk is deemed to be acceptable based on business leadership's [risk appetite](https://www.techtarget.com/searchsecurity/definition/What-is-risk-appetite), no further treatment is necessary.
* Risk sharing or transfer. This involves sharing some of the potential impact of a risk with another entity, such as an insurance firm or an external service provider -- or, if possible, completely transferring responsibility for the risk to that entity.
* Risk mitigation and control. Where practical, various [risk mitigation](https://www.techtarget.com/searchdisasterrecovery/definition/risk-mitigation) measures and management, technical and administrative controls can be applied to help reduce the likelihood or impact of each risk to an acceptable level.
* Risk avoidance. If none of the other options are feasible, risk managers must implement [risk avoidance](https://www.techtarget.com/searchsecurity/definition/risk-avoidance) measures to eliminate the activities or exposures that would enable a particular risk scenario.



## 5. Monitoring&#x20;



For the latter, monitoring risks activities requires a focus on the following areas:

* Effectiveness
* Change
* Compliance

### Effectiveness Monitoring

Responding to an assessed risk does not mark the end of the story. A solution might be effective now but might become ineffective in the future.

Consider the following example: there is always a risk that employees might use weak passwords, which would threaten the whole network. Specific password complexity requirements are enforced to mitigate this risk. This solution should work excellently, shouldn’t it? However, while monitoring the effectiveness of this measure, you might discover that many employees are resorting to writing their complex passwords on sticky notes. Such discovery shows that the implemented control, i.e., password complexity, has become ineffective.

Without effectiveness monitoring, there is no way to discover whether a control is still effective and whether a risk is still mitigated correctly.

### Monitoring Change

“Change is the only constant in life.” as Heraclitus, a Greek philosopher, is quoted as saying. When it comes to risk monitoring, changes might be due to one of the following:

* Change in business
* Change in information systems

Business change might include opening new branches, creating new positions, and acquiring other companies. Any business change might introduce new risks and render existing controls invalid.

The more noticeable change is the change in information systems. Adding new equipment or migrating to new systems would introduce new risks. Consequently, monitoring such changes is necessary to assess unknown risks that have arisen.

### Compliance Monitoring

New laws might see light, new regulatory requirements might come into effect, and new policies might be enforced. Although the pace of change is not as fast as in other areas, these are still areas that the risk management team need to keep an eye on and monitor.

Another aspect that needs to be monitored is the audit findings. Failing to address audit findings can result in fines or stir legal action.



### RISK MANAGEMENT STRATEGIES

The result of a quantitative or qualitative analysis is a measure of inherent risk. Inherent risk is the level of risk before any type of mitigation has been attempted.

In theory, security controls or countermeasures could be introduced to address every risk factor. The difficulty is that security controls can be expensive, so you must balance the cost of the control with the cost associated with the risk. It is not possible to eliminate risk; rather the aim is to mitigate risk factors to the point where the organization is exposed only to a level of risk that it can afford. The overall status of risk management is referred to as risk posture. Risk posture shows which risk response options can be identified and prioritized. For example, you might identify the following priorities:

* Regulatory requirements to deploy security controls and make demonstrable efforts to reduce risk. Examples of legislation and regulation that mandate risk controls include SOX, HIPAA, Gramm-Leach-Bliley, the Homeland Security Act, PCI DSS regulations, and various personal data protection measures.
* High value asset, regardless of the likelihood of the threat(s).
* Threats with high likelihood (that is, high ARO).
* Procedures, equipment, or software that increase the likelihood of threats (for example, legacy applications, lack of user training, old software versions, unpatched software, running unnecessary services, not having auditing procedures in place, and so on).&#x20;

Risk mitigation (or remediation) is the overall process of reducing exposure to or the effects of risk factors. If you deploy a countermeasure that reduces exposure to a threat or vulnerability that is risk deterrence (or reduction). Risk reduction refers to controls that can either make a risk incident less likely or less costly (or perhaps both). For example, if fire is a threat, a policy strictly controlling the use of flammable materials on site reduces likelihood while a system of alarms and sprinklers reduces impact by (hopefully) containing any incident to a small area. Another example is offsite data backup, which provides a remediation option in the event of servers being destroyed by fire.



#### RISK AVOIDANCE AND RISK TRANSFERENCE

Avoidance means that you stop doing the activity that is risk-bearing. For example, a company may develop an in-house application for managing inventory and then try to sell it. If while selling it, the application is discovered to have numerous security vulnerabilities that generate complaints and threats of legal action, the company may make the decision that the cost of maintaining the security of the software is not worth the revenue and withdraw it from sale. Obviously this would generate considerable bad feeling among existing customers. Avoidance is not often a credible option.

Transference (or sharing) means assigning risk to a third party, such as an insurance company or a contract with a supplier that defines liabilities. For example, a company could stop in-house maintenance of an e-commerce site and contract the services to a third party, who would be liable for any fraud or data theft. Specific cybersecurity insurance or cyberliability coverage protects against fines and liabilities arising from data breaches and DoS attacks.



#### RISK ACCEPTANCE AND RISK APPETITE

It is not possible to reduce risks to zero, so part of risk posture is concerned with managing what risks remain.

#### Risk Acceptance <a href="#id-54ce6df0-35c6-48b6-aba0-322f280e0cb0" id="id-54ce6df0-35c6-48b6-aba0-322f280e0cb0"></a>

#### Residual Risk and Risk Appetite <a href="#cefce5e9-c242-4a36-85f8-7b2d3865d3c8" id="cefce5e9-c242-4a36-85f8-7b2d3865d3c8"></a>

Where inherent risk is the risk before mitigation, residual risk is the likelihood and impact after specific mitigation, transference, or acceptance measures have been applied. Risk appetite is a strategic assessment of what level of residual risk is tolerable. Risk appetite is broad in scope. Where risk acceptance has the scope of a single system, risk appetite has a project- or institution-wide scope. Risk appetite is constrained by regulation and compliance.

#### Control Risk <a href="#id-70efc780-faeb-443f-bbc9-da68cdc20212" id="id-70efc780-faeb-443f-bbc9-da68cdc20212"></a>

Control risk is a measure of how much less effective a security control has become over time. For example, antivirus became quite capable of detecting malware on the basis of signatures, but then less effective as threat actors started to obfuscate code. Control risk can also refer to a security control that was never effective in mitigating inherent risk. This illustrates the point that risk management is an ongoing process, requiring continual reassessment and re-prioritization.



## RISK AWARENESS

To ensure that the business stakeholders understand each risk scenario, you should articulate it such that the cause and effect can clearly be understood by the owner of the asset. A DoS risk should be put into plain language that describes how the risk would occur and, as a result, what access is being denied to whom, and the effect to the business. For example: "As a result of malicious or hacking activity against the public website, the site may become overloaded, preventing clients from accessing their client order accounts. This will result in a loss of sales for so many hours and a potential loss of revenue of so many dollars."

A risk register is a document showing the results of risk assessments in a comprehensible format. The register may resemble the heat map risk matrix shown earlier with columns for impact and likelihood ratings, date of identification, description, countermeasures, owner/route for escalation, and status. Risk registers are also commonly depicted as scatterplot graphs, where impact and likelihood are each an axis, and the plot point is associated with a legend that includes more information about the nature of the plotted risk. A risk register should be shared between stakeholders (executives, department managers, and senior technicians) so that they understand the risks associated with the workflows that they manage.



## BUSINESS IMPACT ANALYSIS

Business impact analysis (BIA) is the process of assessing what losses might occur for a range of threat scenarios. For instance, if a DDoS attack suspends an e-commerce portal for five hours, the business impact analysis will be able to quantify the losses from orders not made and customers moving permanently to other suppliers based on historic data. The likelihood of a DoS attack can be assessed on an annualized basis to determine annualized impact, in terms of costs. You then have the information required to assess whether a security control, such as load balancing or managed DDoS mitigation, is worth the investment.

Where BIA identifies risks, business continuity planning (BCP) identifies controls and processes that enable an organization to maintain critical workflows in the face of some adverse event.





## IDENTIFICATION OF CRITICAL SYSTEMS

To support the resiliency of mission essential and primary business functions, it is crucial to perform an identification of critical systems. This means compiling an inventory of business processes and the assets that support them. Asset types include:

* People (employees, visitors, and suppliers).
* Tangible assets (buildings, furniture, equipment and machinery (plant), ICT equipment, electronic data files, and paper documents).
* Intangible assets (ideas, commercial reputation, brand, and so on).
* Procedures (supply chains, critical procedures, standard operating procedures).

For mission essential functions, it is important to reduce the number of dependencies between components. Dependencies are identified by performing a business process analysis (BPA) for each function. The BPA should identify the following factors:

* Inputs—the sources of information for performing the function (including the impact if these are delayed or out of sequence).
* Hardware—the particular server or data center that performs the processing.
* Staff and other resources supporting the function.
* Outputs—the data or resources produced by the function.
* Process flow—a step-by-step description of how the function is performed.



## SINGLE POINTS OF FAILURE

Each IT system will be supported by hardware assets, such as servers, disk arrays, switches, routers, and so on. Reducing dependencies means the system design can more easily eliminate the sort of weakness that comes from these devices becoming single points of failure (SPoF). A SPoF is an asset that causes the entire workflow to fail if it is damaged or otherwise not available. SPoFs can be mitigated by provisioning redundant components. Metrics for asset reliability can help to determine when and how much redundancy is required. Some of the main KPIs relating to service availability are as follows:

* Mean time to failure (MTTF) and mean time between failures (MTBF) represent the expected lifetime of a product. MTTF should be used for non-repairable assets. For example, a hard drive may be described with an MTTF, while a server (which could be repaired by replacing the hard drive) would be described with an MTBF. You will often see MTBF used indiscriminately, however. For most devices, failure is more likely early or late in life, producing the so-called "bathtub curve."\
  \
  MTTF/MTBF can be used to determine the amount of asset redundancy a system should have. A redundant system can failover to another asset if there is a fault and continue to operate normally. It can also be used to work out how likely failures are to occur.
* The calculation for MTBF is the total time divided by the number of failures. For example, if you have 10 devices that run for 50 hours and two of them fail, the MTBF is 250 hours (10\*50)/2.
* The calculation for MTTF for the same test is the total time divided by the number of devices, so (10\*50)/10, with the result being 50 hours.
* Mean time to repair (MTTR) is a measure of the time taken to correct a fault so that the system is restored to full operation. This can also be described as mean time to "replace" or "recover." This metric is important in determining the overall recovery time objective (RTO).

## DISASTERS

In terms of business continuity, a disaster is an event that could threaten mission essential functions. For example, a privacy breach is a critical incident, but it is probably not a direct threat to business functions. An earthquake that destroys a data center is a disaster-level event. Disaster response involves many of the same principles and procedures as incident response, but at a larger scale.

#### Internal versus External <a href="#e399e422-fa88-4ace-a20b-0ca937a93296" id="e399e422-fa88-4ace-a20b-0ca937a93296"></a>

#### Person-Made <a href="#c354ea6c-e092-4cd2-9f10-62dbf8d365c4" id="c354ea6c-e092-4cd2-9f10-62dbf8d365c4"></a>

A person-made disaster event is one where human agency is the primary cause. Typical examples other than devastating cybersecurity incidents include terrorism, war, vandalism, pollution, and arson. There can also be accidental person-made disasters, such as cutting through power or telecoms cabling.

#### Environmental <a href="#aa382c58-c608-4c60-b4bd-86a7ed2c28fc" id="aa382c58-c608-4c60-b4bd-86a7ed2c28fc"></a>

An environmental disaster, or natural disaster, is one that could not be prevented through human agency. Environmental disasters include river or sea floods, earthquakes, storms, disease, and so on. Natural disasters may be quite predictable (as is the case with areas prone to flooding or storm damage) or unexpected, and therefore difficult to plan for.





#### Site Risk Assessment <a href="#id-4c8147f9-237b-4ae9-b597-4d7557abb5fb" id="id-4c8147f9-237b-4ae9-b597-4d7557abb5fb"></a>

Where cybersecurity generally has financial impacts, site safety can have impacts to life and property. A site risk assessment evaluates exposure to the following types of factor:

* Risk from disaster events, such as earthquake, flood, and fire. These events can occur naturally or from person-made causes.
* Risk from disruption to utilities, such as electricity, water, and transportation. These risks are higher in geographically isolated sites.
* Risk to health and safety from on-premises electromechanical systems or chemicals.

## DISASTER RECOVERY PLANS

Disaster recovery plans (DRPs) describe the specific procedures to follow to recover a system or site to a working state following a disaster-level event. The DRP should accomplish the following:

1. Identify scenarios for natural and non-natural disaster and options for protecting systems. Plans need to account for risk (a combination of the likelihood the disaster will occur and the possible impact on the organization) and cost.\
   \
   There is no point implementing disaster recovery plans that financially damage the organization. The business case is made by comparing the cost of recovery measures against the cost of downtime. The recovery plan should not generally exceed the downtime cost.
2. Identify tasks, resources, and responsibilities for responding to a disaster.

* Who is responsible for doing what? How can they be contacted? What happens if they are not available?
* Which functions are most critical? Where should effort first be concentrated?
* What resources are available? Should they be pre-purchased and held in stock? Will the disaster affect availability of supplies?
* What are the timescales for resumption of normal operations?

1. Train staff in the disaster planning procedures and how to react well to change.

As well as restoring systems, the disaster recovery plan should identify stakeholders who need to be informed about incidents with impacts to life and safety. There may be a legal requirement to inform the police, fire service, or building inspectors about any safety-related or criminal incidents. If third-party or personal data is lost or stolen, the data subjects may need to be informed. If the disaster affects services, customers need to be informed about the time-to-fix and any alternative arrangements that can be made.





## FUNCTIONAL RECOVERY PLANS

Because disasters are extreme and (hopefully) rare events, it is very difficult to evaluate how effective or functional a recovery plan is. There are four principal methods for assessing the functionality of recovery plans:

* Walk-throughs, workshops, and orientation seminars—often used to provide basic awareness and training for disaster recovery team members, these exercises describe the contents of DRPs, and other plans, and the roles and responsibilities outlined in those plans.
* Tabletop exercises—staff "ghost" the same procedures as they would in a disaster, without actually creating disaster conditions or applying or changing anything. These are simple to set up but do not provide any sort of practical evidence of things that could go wrong, time to complete, and so on.
* Functional exercises—action-based sessions where employees can validate DRPs by performing scenario-based activities in a simulated environment.
* Full-scale exercises— action-based sessions that reflect real situations, these exercises are held onsite and use real equipment and real personnel as much as possible. Full-scale exercises are often conducted by public agencies, but local organizations might be asked to participate.
