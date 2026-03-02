graph TD
    subgraph Jaringan_Luar [Internet / Host]
        Host[Laptop/Host OS]
    end

    subgraph Internal_Network [Internal Network - 10.10.10.0/24]
        adm01[adm01 <br/> 10.10.10.10]
        srv01[srv01 <br/> 10.10.10.11]
        cli01[cli01 <br/> 10.10.10.12]
    end

    Host -- SSH via NAT/Port Forward --> adm01
    adm01 -- Management SSH Key-Only --> srv01
    adm01 -- Management SSH Key-Only --> cli01
    srv01 -. Ping .- cli01


