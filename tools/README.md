#### Puppet - Configuration Manager
In computing, Puppet is an open-source configuration management tool. It runs on many Unix-like systems as well as on Microsoft Windows, and includes its own declarative language to describe system configuration.

#### Chef 
Chef is a systems and cloud infrastructure automation framework that makes it easy to deploy servers and applications to any physical, virtual, or cloud location, no matter the size of the infrastructure.

#### Ansible
Ansible is a free-software platform for configuring and managing computers which combines multi-node software deployment, ad hoc task execution, and configuration management.[1] It manages nodes (Linux nodes must have Python 2.4 or later installed on them, Windows nodes require PowerShell 3.0 or later) over SSH or over PowerShell.[2] Modules work over JSON and standard output and can be written in any programming language. The system uses YAML to express reusable descriptions of systems.[3]

#### Sensu - Monitoring


#### Consul - Configuration Manager

Nodelarda çalışan ve çalıştığı nodelar hakkında bilgi toplayan ve konfigure edilmeyen imkan sağlayan uygulama. 

**_Consul has multiple components, but as a whole, it is a tool for discovering and configuring services in your infrastructure._**

Yapısında bulunan şeyler;

1. **Client**
Client düşük bandwith tüketen sadece health check için kullanılan consul clientidir
2. **Server**
Nodeların haberleşmelerini yöneten yapıdır
3. **Consensus**
[https://en.wikipedia.org/wiki/Consensus_(computer_science)](https://en.wikipedia.org/wiki/Consensus_(computer_science))
Distrubuted mimaride tek veriye birden fazla yapı ulaşmak istediği durumların yönetilmesini konu alır. Bu gibi durumlarda hata olmasına veya inconsistent veri olmasına karşılık olarka fault tolerance olmalıdır sistem.
4. **Gossip**
Ağda bağlı bulunan nodelar arası **_health checking_**, **_status_** tarzı bilgilerin paylaşıldığı yapı

![image](https://www.consul.io/assets/images/consul-arch-5d4e3623.png)

### Scout2

Scout2 is a security auditing tool for AWS environments. Instead of manually navigating through web pages, you can rely on Scout2 to fetch all the configuration data of an AWS environment for you; it even generates an attack surface report. Scout2 ships with preconfigured rules and can be easily extended to support more services and test cases. Since Scout2 only performs AWS API calls to fetch configuration data and identify security gaps, it is not necessary to complete and submit the AWS Vulnerability / Penetration Testing Request Form.

### Contentful

CMS platform is feed from different sources.