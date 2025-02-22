# CTE-Common-Table-Expression-in-SQL---Layman-Explanation

CTE ka kaam temporary table bananay jaisa hota hai jo sirf ek query ke liye use hoti hai. Ye aapki SQL query ko zyada readable, organized aur efficient banata hai.

CTE Ka Basic Structure
CTE likhnay ka tareeqa kuch is tarah hota hai:

    WITH CTE_Name AS (  
      -- Yeh temporary table hai jo data store Karega  
      SELECT column1, column2  
      FROM SomeTable  
       WHERE condition  )  
-- Is query mein CTE ka use hoga  

    SELECT * FROM CTE_Name;  

CTE Ka Kaam Step by Step

  - CTE Pehlay Execute Hota Hai → Jo bhi logic aap WITH ke andar likho ge, wo pehlay execute hoga.
  - CTE Ek Temporary Table Banata Hai → Ismein sirf usi query ka data hota hai jo WITH ke andar likha hota hai.
  - CTE Sirf Ek Query Ke Liye Available Hota Hai → Jaise hi query khatam hoti hai, CTE ka data bhi delete ho jata hai.
  - CTE Ka Faida Yeh Hai Ke Aap Query Ko Multiple Daafa Use Kar Sakte Ho → Bina subqueries likhnay ki zaroorat ke.

Example 1: CTE Ka Simple Use (Average Energy Se Zyada Products Dikhana)

    WITH AvgEnergy AS (  
      SELECT AVG(energy) AS avg_energy FROM McDonald  )  
      SELECT Product_name, energy  
      FROM McDonald  
      WHERE energy > (SELECT avg_energy FROM AvgEnergy);
      
Kya Ho Raha Hai?

  - CTE (AvgEnergy) Average Energy Calculate Kar Raha Hai.
  - Phir McDonald Table Se Wo Products Nikale Jaa Rahe Hain Jinki Energy Avg Se Zyada Hai.
  - Iska Faida Yeh Hai Ke AVG(energy) Ko Bar Bar Calculate Nahi Karna Pada, CTE Ne Ye Ek Dafa Hi Calculate Karke Store Kar Liya.


