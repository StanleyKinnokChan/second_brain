# Interoperability (work with 3rd party)

<aside>
💡 **Interoperability** is the ability of different systems, devices, applications or products to connect and communicate in a coordinated way, without effort from the end user.

</aside>

- R53 can do both domain register + Hosting
- What R53 did normally
    - accepts your money (domain registration fee)
    - allocates 4 name servers (domain hosting)
    - creates a zone file on the above NS (domain hosting)
    - communicates with the registry of the TLD (Domain registrar)

        [[Interoperability (work with 3rd party]]%207c006c98cab146d09aa9136f9860203f/Untitled.png)

- but we can split them and only do one of them using R53

**Registrar only (not really worth it and rarely)**

[[Interoperability (work with 3rd party]]%207c006c98cab146d09aa9136f9860203f/Untitled%201.png)

**Hosting only (common)**

[[Interoperability (work with 3rd party]]%207c006c98cab146d09aa9136f9860203f/Untitled%202.png)
