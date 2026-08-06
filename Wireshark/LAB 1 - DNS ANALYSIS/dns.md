# Lab 2 – DNS Analysis
* DNS(Domain Name System)
## Objective

Understand how DNS resolves domain names.

## Steps

1. Start **Wireshark**.
2. Visit the following websites:

   * google.com
   * youtube.com
   * github.com
3. Stop the capture.

4. Apply a Display Filter : `dns`

## Questions

1. Which DNS server responded?
2. What IP address was returned?
3. Was an **A** or **AAAA** record used?

## Answers

### [1] Which DNS Server Responded?

* Apply the following display filter:

  `dns`

* Find a packet that says **"Standard query response"**.

* Click on the packet.

* Look at the **Source** column in the packet list.

* The IP address shown in the **Source** column is the DNS server that responded.

**Screenshot:**
<img alt="clouds_above_a_mountain" src="C:\cyberr\Wireshark\Lab 1 - DNS Analysis\Screenshot 2026-07-31 120606.png"><br/><br/> 

### [2] What IP Address Was Returned?

* Select the **DNS response packet**.
* Expand **Domain Name System (response)** in the packet details.
* Look for the **Answers** section.
* You will see the IP address returned by the DNS server.

**Screenshot:**
<img alt="clouds_above_a_mountain" src="C:\cyberr\Wireshark\Lab 1 - DNS Analysis\Screenshot 2026-07-31 130419.png"><br/><br/> 

### [3] Was an A or AAAA Record Used?

* An **A record** maps a domain name to an **IPv4 address**.

  **Example:**
  `google.com → A → 142.250.183.78`

* An **AAAA record** maps a domain name to an **IPv6 address**.

  **Example:**
  `google.com → AAAA → 2404:6800:4007:80d::200e`

## Learning

DNS translates domain names into IP addresses. It allows users to access websites using easy-to-remember domain names instead of numerical IP addresses.
