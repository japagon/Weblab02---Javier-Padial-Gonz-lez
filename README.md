Web Infrastructure Lab: DNS and Apache Security
This project demonstrates how to set up a network with two servers using Vagrant and VirtualBox. It includes a DNS server and a Web server with different types of authentication.

Project Structure
Machine 1 (dns): A DNS server using BIND9.

Machine 2 (tierra): An Apache Web server with restricted areas.

Step-by-Step Implementation
1. Infrastructure Setup
I used a Vagrantfile to automate the creation of two Debian Bullseye virtual machines.

DNS IP: 192.168.56.100

Web IP: 192.168.56.101

2. DNS Configuration
I installed BIND9 on the DNS machine. I configured the zone sistema.sol and added a CNAME record so that discovery.sistema.sol points to the Web server.

3. Web Server Setup
I installed Apache2 on the tierra machine. I created a Virtual Host for the domain discovery.sistema.sol.

4. Security and Authentication
I configured two levels of security for the website:

Basic Authentication: I created a .htpasswd_basic file for users arturo, ana, and maria.

Groups: I used a .htgroups file to allow only the "ventas" group to see the /ventas folder and the "desarrollo" group to see the /desarrollo folder.

Digest Authentication: I enabled the auth_digest module and created a protected area for the user commander.

5. Testing the Lab
I verified the project using curl commands from the terminal:

DNS Test: nslookup discovery.sistema.sol.

Access Test: curl -u arturo:arturo http://discovery.sistema.sol/basic/ventas/index.html (returns 200 OK).

Digest Test: curl --digest -u commander:commander http://discovery.sistema.sol/digest/index.html (returns 200 OK).

How to use this project
Clone the repository.

Open your terminal in the project folder.

Run vagrant up.

Wait for the machines to be ready.
