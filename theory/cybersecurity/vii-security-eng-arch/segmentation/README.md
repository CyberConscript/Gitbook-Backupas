# Segmentation

## Small scale

All in one decive acting as gateway. It also includes management function. This architecture is appropriate for the smallest environments that require protection, but lacks budged.

<figure><img src="../../../../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>

To decrease burned from one device and somewhat separate management from gateway alternative could be built in this way

<figure><img src="../../../../.gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>

The advantage of this approach is the ability to manage many gateways from a common management server using a common object database. Even when the management is down, gateway still operates and collects logs waiting for it to sent to management server later.



## Medium scale&#x20;

Including SIEM or other advanced event viewer. It is separated from other virtual and physical machines. Also better to directly get logs from log servers and only security team member could reach it from dedicated machine.

&#x20;

<figure><img src="../../../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

## Large scale

When there is a high number of machines it is better to logicaly separate sites for high availability and decrease  load from highly loaded points.

<figure><img src="../../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
