# Respond to Risk

Risk management’s third component focuses on how organizations respond to the risks identified through risk assessment. What are the possible responses to risks?

* Avoid Risk
* Transfer Risk (or Share Risk)
* Mitigate Risk (or Reduce Risk)
* Accept Risk

The response you choose against the risk takes into account the severity of the threat, the probability of occurrence, and the costs of the possible countermeasures. Let’s cover each in more detail.

* **Avoid Risk**: If a company decides to eliminate the activity that leads to the risk, that would be risk avoidance. A bank might decide that all employees’ computers cannot access the Internet to protect its systems against all online threats. An organisation might instruct its employees to work exclusively using the workstations on its premises to prevent data from being stolen.
* **Transfer Risk**: A company might consider the risk too high to handle, so it decides to purchase insurance. That would be risk transference or risk sharing. A publishing house might buy insurance against fire, for instance.
* **Mitigate Risk**: A company might invest in countermeasures to reduce risk to an acceptable level; this would be risk mitigation. To protect against computer viruses, a company might install antivirus on all its computers instead of blocking access to the Internet and glueing the USB ports.
* **Accept Risk**: Sometimes, the countermeasure cost exceeds the loss incurred if the risk is realised.

It is important to stress that “Ignore Risk” is not a valid choice. Accepting a risk does not mean the risk is ignored. It means the risk is analysed along with its impact and countermeasures; however, some reasons justify keeping things unchanged. One reason might be that the countermeasure is too expensive compared to the potential loss. Another reason might be that implementing a countermeasure would significantly alter the business process.

### Quantitative Analysis

Quantitative risk analysis would help us decide whether a specific control is justified from the business perspective. Implementing a safeguard won’t make sense unless its benefit outweighs its cost.

Consider again our example of the risk of a laptop getting infected by ransomware. Can we mitigate this risk? We are considering setting up antivirus software on all laptops. The cost is $120 per laptop annually, including the licensing and extra staff hours.

We need to decide whether this countermeasure is justified from the business perspective. To do that, we need to calculate the value of the safeguard. **It would be justified from the business perspective only if the value of the safeguard is positive.** The value of the safeguard to the organisation is calculated as follows:

$$ValueofSafeguard = ALEbeforeSafeguard − ALEafterSafeguard − AnnualCostSafeguard$$

We have already calculated ALE before the safeguard is implemented.

$$ALEbeforeSafeguard = SLEbeforeSafeguard × ARObeforeSafeguard = $9000 × 0.5 = $4, 500$$.

Let’s calculate ALE after the safeguard is added:

$$ALEafterSafeguard = SLEafterSafeguard × AROafterSafeguard$$

We might need to recalculate SLE in case the implemented safeguard affected the exposure factor (EF):

$$SLEafterSafeguard = AssetValue × EFafterSafeguard$$

In this case, the exposure factor (EF) is not expected to change. In other words, installing an antivirus won’t change the damage that a ransomware infection would cause. Consequently, SLE remains the same after the safeguard is implemented:

$$SLEafterSafeguard = AssetValue × EFafterSafeguard = $10, 000 × 90% = $9, 000$$.

However, an antivirus would significantly decrease the annualised rate of occurrence (ARO). Let’s say that this antivirus is so efficient that we expect that ARO to become 0.02.

Now we can calculate ALE after the safeguard is added.

$$ALEafterSafeguard = SLEafterSafeguard × AROafterSafeguard = $9, 000 × 0.02 = $180$$.

We already estimated the safeguard cost to be $120 per year. Therefore,

$$ValueofSafeguard = $4, 500 − $180 − $120 = $4, 200$$.

Because the value of the selected safeguard is positive, we conclude that it is justified from the business perspective. In other words, from the risk analysis perspective, installing an antivirus has a value (benefit) of $4,200 to the organisation.

If the value of the safeguard turns out to be negative, it means that the cost of the safeguard outweighs its benefits. Consequently, it won’t be justified from a business perspective.



<figure><img src="../../../../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>
