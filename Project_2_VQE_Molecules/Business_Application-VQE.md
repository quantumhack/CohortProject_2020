![CDL 2020 Cohort Project](../figures/CDL_logo.jpg)
# Quantum Cohort Project Business Application

For each weekly project, your team is asked to complete the below business application exercise.
To complement the technical tasks, please consdier the four questions below.
You are free to format your response to these four questions as you wish (with the final question done as a short recorded video), and to include
the content (or links to the content) on your forked repository.

## Step 1: Explain the technical problem you solved in this exercise

The main goal of this exercise was to implement VQE in order to find the parameters that generate the fundamental state of different molecules in a quantum circuit. This included the following tasks:

- In the first task, we reviewed different approximations commonly used for estimating analytically the ground state of a many body system. These included:
    - Hartree Fock, where a single Slater determinant is proposed (no correlations)
    - Coupled Cluster methods, which are a refinement of Hartree Fock where one and two body operators are considered.
    - We also considered exact solutions, known as Full configuration interactions, where all interactions are considered.
    ![LiH](../LiH.jpg)
- Then we analysed the corresponding qubit Hamiltonian using Jordan Wigner. The tapering technique was introduced to lower the complexity of the resulting operator by exploiting symmetries.
- In order to use VQE, we must generate the unitaries. In this task we explored 2 types, choosing between sto-3g and sto-6g basis depending on the molecule and its complexity:
    - Unitary Coupled Cluster: a direct generalization of the Coupled Cluster method. This is a “fermionic” approach.
    - Qubit Coupled Cluster: we look directly to the qubit space, optimized for a quantum circuit. This method is better for translating to existing hardware.
- In order to measure the expectation value of the Hamiltonian, complicated measures have to be made. We explored how to partition these operators into a minimal number of groups such that each member can be fully measured at the same time.
- In this final step, we converted the unitaries obtained in previous steps to gate-based algorithms able to run in existing hardware. 
We performed this task for H2, LiH and H4. Additionally, further challenges were addressed.
- We explored the framework Qulacs to simulate noise aware quantum systems in order to find the first excited state of a H2 molecule, by using VQE and orthogonality with the fundamental state.
- We analyzed and solved the Max-Cut problem with VQE. This problem is known to be NP-complete and can be significantly sped up with hybrid methods.

## Step 2: Explain or provide examples of the types of real-world problems this solution can solve

Applications of optimizing molecular data simulation:
- **Pharmaceutical & Materials Science applications**: optimizing drug and molecule discovery 
    - Advantages for expanding and speeding up drug and molecule discovery R&D:
        - Molecular structure analysis for complex molecules useful for chemical and drug R&D
        - Protein design using unconstrained discrete optimization [[1]](https://www.zapatacomputing.com/solutions/) [[2]](https://www.sciencedirect.com/science/article/pii/S0004370214000332)
        - Simulations for molecular binding affinity prediction in drug discovery [[1]](https://www.zapatacomputing.com/solutions/) [[4]](https://link.springer.com/article/10.1007/s10822-010-9363-3)
        - Transition state analysis for catalytic reaction simulation [[1]](https://www.zapatacomputing.com/solutions/) [[5]](https://pubs.acs.org/doi/abs/10.1021/jp020326p?casa_token=SMtIra4cJp8AAAAA:aaeP5ToKdgk_0pbqIG-KrYsixjmVuJuSSE-q0Tf-Rgc4pURIpx1DhilqmoLIAI7OLZoKpiZKe7uKT1fw)
        - Determination of the crystalline structure of organic molecules [[1]](https://www.zapatacomputing.com/solutions/) [[6]](https://link.springer.com/content/pdf/10.1007/978-3-319-05774-3.pdf) [[7]](https://www.nature.com/articles/ncomms1451.)
        - Molecular screening in drug discovery using continuous latent space [[1]](https://www.zapatacomputing.com/solutions/) [[3]](https://bmcbiol.biomedcentral.com/articles/10.1186/1741-7007-9-71)
        - Minimizes the massive R&D costs used to search for novel molecules by exponentially reducing the number of data points necessary for simulations
    - Quantum Computing implementation (future research expansion):
        - Additionally, with more advanced quantum computing hardware, drug development times could be **sped up by 20%** and **drug approval rates could double** using similar molecular simulation optimizations [[BCG, 2019]](https://www.bcg.com/en-us/publications/2018/coming-quantum-leap-computing.aspx)
            - We will have a stake in the quantum advantage by expanding research to be compatible with quantum resources, like our D-Wave optimization work


- Other industries (financial, telecom, energy, etc.) have the potential to benefit from the optimization with further work to effectively map their complex data sets into a Hamiltonian. 



## Step 3: Identify at least one potential customer for this solution - ie: a business who has this problem and would consider paying to have this problem solved


**Market Opportunity:** The Boston Consulting Group [[BCG, 2019]](https://www.bcg.com/en-us/publications/2018/coming-quantum-leap-computing.aspx) predicts that quantum simulations could represent an addressable market in pharmaceuticals of up to **$20 billion** by 2030 with **another $7 billion** coming from chemicals, materials science, and other materials science–intensive industries. 
    

**Target Customers:** Pharmaceutical, chemical, and materials science companies with high R&D costs, who closely align innovation with business strategy

- Big Pharma
    - Pfizer
        - Revenue: $52 billion [[Pfizer 10-K, 2019]](http://d18rn0p25nwr6d.cloudfront.net/CIK-0000078003/dee171a3-b766-46e8-a807-dab4c7fb1895.pdf)
        - R&D: $8.7 billion (85% of costs)
    - Roche
        - Revenue: $65 billion [[Roche Annual Report, 2019]](https://www.roche.com/dam/jcr:a3545548-a7f9-40f4-a70e-7266a363f856/en/ar19e.pdf)
        - R&D: $12.4 billion (30% of costs)
    - Merck
        - Revenue: $47 billion [[Merck 10-K, 2020]](http://d18rn0p25nwr6d.cloudfront.net/CIK-0000064978/75a322e0-ce26-478b-954f-5da950e9d365.pdf)
        - R&D: $9.9 billion (70% of costs)
    
- Big Chemicals & Materials Science Companies
    - BASF 
        - Revenue: $67 billion [[BASF Annual Report, 2019]](https://www.basf.com/global/documents/en/news-and-media/publications/reports/2020/BASF_Report_2019.pdf)
        - R&D: $5.9 billion (22% of costs) 
    - 3M
        - Revenue: $31 billion [[3M 10-K, 2020]](http://d18rn0p25nwr6d.cloudfront.net/CIK-0000066740/d02f076e-a2bb-49af-b19b-ad4aebfd51fb.pdf)
        - R&D: $1.8 billion (11% of costs)
    - DuPont
        - Revenue:$22 billion [[DuPont 10-K, 2019]](https://s23.q4cdn.com/116192123/files/doc_financials/2019/Q4/DuPont-2019-10-K-(Final).pdf)
        - R&D: $955 million (7% of costs) 
    - PetroChina
        - Revenue: $359 billion [[PetroChina Annual Report, 2019]](http://www.petrochina.com.cn/ptr/ndbg/202004/a11e316ca2bd49bab9e2a55a58c02add/files/3a74f5fb90284053ac786919340f41b0.pdf)
        - R&D: $3.1 billion (0.9% of costs) 
    

## Step 4: Prepare a 90 second video explaining the value proposition of your innovation to this potential customer in non-technical language

Link to video:
