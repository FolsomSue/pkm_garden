_This blog was written by a colleague from Tenable._

## What is OT vs. IT?

Modern-day industrial and critical infrastructure organizations rely heavily on the operational technology (OT) environment to produce their goods and services. Beyond traditional IT operations that utilize servers, routers, PCs and switches, these organizations also rely on OT, such as programmable logic controllers (PLCs), distributed control systems (DCSs) and human machine interfaces (HMIs) to run their physical plants and factories. While OT devices have been in commercial use for more than 50 years, a complete transformation has occurred, changing the way we operate, interact with, and secure the OT environment.

## Should OT and IT be converged?

Many organizations have opted to converge their IT and OT environments, which can yield many benefits such as efficiency and more elegant architecture; at the same time, these decisions are not without risk. Convergence can produce new attack vectors and attack surfaces; it can result in breaches that start on one side of the converged infrastructure and laterally creep to the other, from IT to OT and vice versa.  For example, the recent ransomware that leverages IT/OT convergence including the manufacturing and energy industries has prompted CISA to issue guidance regarding ransomware impacting OT environments ([read](https://www.tenable.com/whitepapers/alignment-with-dhs-guidance-on-ransomware-june-2021-bulletin) the guidance and how Tenable can help).

![it and ot risk](https://cdn-cybersecurity.att.com/blog-content/IT_OT_Risk.png)

Threats that impact OT operations are not the same as those that impact IT environments, thus the required security tools and operating policies are different. Endpoints can’t use traditional security tools. However, deploying the right technologies can harness all the benefits of a converged operation without increasing the security exposure profile of the organization. It is important for organizations to establish a carefully planned strategy prior to any convergence initiative, rather than bolting on security as an afterthought.

## Air gapping OT – is it the right approach?

What happens when a business makes the strategic decision to NOT converge their IT and OT operations? Many organizations follow this path for a variety of reasons including strategic, technical and business factors. By keeping IT and OT systems separate, these organizations are implementing an “air gap” security strategy. Traditionally, air gapping OT operations has been viewed as the gold standard when it comes to industrial and critical infrastructure environments. Operating as a “closed loop” without any interfaces to the outside world, the OT infrastructure is physically sequestered from any external environment. With no data traveling outside the environment, and nothing from outside coming in, this buffer is viewed as the ultimate methodology in securing an organization from security threats.

While the notion of air gapping seems simple enough, it is extremely difficult to maintain. Simply cutting connections is only part of maintaining a sterile environment, and there are many other paths into what is supposedly an isolated infrastructure. For example, true isolation requires the elimination of electromagnetic radiation from the devices in an OT infrastructure; this requires the implementation of a massive faraday cage to eliminate potential leakage vectors.

Over the years, additional attack vectors have been discovered, including FM frequency signals from a computer to a mobile phone; thermal communication channels between air gapped computers; the exploitation of cellular frequencies; and near-field communication (NFC) channels. Even LED light pulses among OT equipment have exposed critical systems to malicious activity. There are countless examples of highly-enforced air gapped facilities that have suffered a breach due to something as simple and seemingly innocuous as an external laptop being used as an HMI, or a USB thumb drive used for OT purposes.

In an average OT environment, upwards of 20 percent of the infrastructure comprises IT equipment. For organizations that have implemented an [Industry 4.0 initiative](https://www.business.att.com/learn/tech-advice/how-5g-will-revolutionize-manufacturing.html), such as industrial IoT, the amount of IT-related equipment can balloon to 40 percent of the OT infrastructure.

Organizations that have no specific initiatives for IT and OT convergence are among the most at risk because no additional security is implemented beyond air gapping.

Securing operations requires more than building a digital moat around the OT infrastructure. Even under the most favorable of circumstances, this isolation is nearly impossible to maintain. The introduction of one seemingly harmless variable into a sterile environment can permanently destroy the most stringently enforced air gap. This is known as “accidental convergence.”

## Suggested best practices for IT/OT

In general, IT people are used to working with the latest and greatest hardware and software, including the best security available out there to protect their networks. They tend to spend time patching, upgrading, and replacing systems. Meanwhile, OT staff are used to working with legacy technologies, many of which pre-date the internet era. These often use proprietary network protocols and lack basic security controls like authentication or encryption. They also don't have event logs or audit trails. As a result, incident detection and response in an OT environment is very different than in an IT environment.

Whatever technology is deployed and regardless of the mindset that the individual has been used to, both the IT and OT environments must now come together to address the security threats on both sides of the network. Further, they must collaborate to stop lateral creep of an attack that may have started in one environment and successfully spreads to the other.

While there are significant differences between the words of IT and OT, one thing that can be agreed on are the key elements in establishing a robust security posture when it comes to industrial security. They include:

• Threat Detection that combines behavioral anomalies with policy-based rules.

• Asset tracking that includes dormant devices and goes as deep as PLC backplane configurations.

• Vulnerability management that tracks and scores patch and risk levels of ICS devices.

• Configuration control that tracks all changes to code, OS & firmware regardless

whether done through the network or locally.

• Enterprise visibility to ensure that all data collected integrates to a single pane of glass.

## Conclusion

IT and OT teams must find common ground to eliminate the substantial risk factors of both planned and accidental IT/OT convergence. But the mission does not end there. OT security solutions that work in conjunction with IT security solutions can be the catalyst that not only provides the visibility, security and control needed to thwart new cyberthreats, but also brings these once separate teams together for the common security every manufacturing, critical infrastructure and industrial organization will need to fulfill its core mission efficiently and securely.

If you are interested in learning more on how the power of AT&T and Tenable can help protect your businesses infrastructure, applications and data, please check out [more information](https://cybersecurity.att.com/products/managed-vulnerability-program).