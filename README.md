# Data-Center-Consolidation
	
  # Implemented a consolidation algorithm that deploys redundant virtual machines on different servers across the datacenter in anticipation of host server failure
  # Reduces power consumption in Data Center environment by 25% by turning off inessential physical servers while also ensuring minimum cost flow in the network.
  
  # The input of this program is number of VMs, the switch ports of each physical machine and the copy number for each VM. 
  # By having this data, the total number of physical machine is being calculated.
  # For each PM, first it checks to make sure there is no original copy of any VM on this machine, because if it has even one original VM, it cannot be turned off.
  # Then, it starts calculating the cost of replication of VMS one by one by cosidering all servers.
  # Moving VM replication to this new location should meet all the storage and VM Constraints. This limitation includes the following rules:

    1. It is not possible to have more than one copy of a VM on one physical machine 
    2. It is not possible to copy different VMs on one PM more that its capacity.
    3. Cost of moving to this new location should be the same as cost of moving
       to the original PM.
    4. The new place shouldn’t be already turned off.
    
PSEUDOCODE:

Input: VM replica placement from VM replication algorithm

Output: Number of IPMs.

Notations:

m: Last number of PM
Nipm: number of Inactive PMs that are turned off
TPM: Target PM

Nipm=0 // Initially none of the PMs are turned off
1. for (PM number i = 1 to m)

2. for each of VM on PM number i

3. flag = true;

4. if it can find a TPM

5. move the replica VM to the TPM

6. else

7. flag=false;

8. break;

9. end if;

10. end for;

11. if (flag == true)

12. Nipm ++; /*This CPM can be turned off as all VMs are moved to new locations*/

13. end if;

14. end for;

15. RETURN Nipm. /*Return total number of inactive PMs */

Runs in O(mn) time
