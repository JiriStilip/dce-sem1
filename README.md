# KIV/DCE First Task
Implement several backends and a load balancer infrastructure using Terraform, Ansible and Docker. Use the OpenNebula cloud service provided by University of West Bohemia at nuada.zcu.cz.

## What does it do
The resulting cluster returns a simple web page containing the IP address of the serving backend when accessing the load balancer's address. The backend is written using Python Flask module. The load balancer utilizes round-robin algorithm for purposes of transparency.

## Usage
1. Clone the repository
   `git clone --recursive https://github.com/JiriStilip/dce-task1.git`
2. In `terraform.tfvars`, change the username and login token to valid values
3. Initialize Terraform
   `terraform init`
4. Apply the infrastructure
   `terraform apply` -> `yes`
5. Run the Ansible playbook
   `ansible-playbook -i dynamic_inventories/cluster ansible/task1-cluster.yml`
6. Connect to `http://<load-balancer-ip>`

## Notes
- *the number of backends can be changed using the backend_nodes_count variable in terraform.tfvars*
- *the project uses an existing OS image from nuada.zcu.cz to avoid resource limit problems*
- *don't forget to refresh the page several times to see if the serving backend changes*
- *usage assumes that Git, Docker, Ansible and Terraform are installed and available*
