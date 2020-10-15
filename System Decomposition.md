#### System Decomposition

---

- Partioning
  - Open Architecture (Transparent Layering)
    - Any layer can invoke operations from any layers below
    - Runtime Efficiency 
    - Interface Segregation
    - Backend For Frontend pattern
    - Service Orientation
  - Closed Architecture (Opaque Layering)
    - A layer can only invoke operations from the immediate Layer
    - Sinkhole Anti pattern
      - "More pass through requests"
  - Horizontal Partition : Layered Architecture (Separation of Functionality)
    - A layer can only depend on lower layers
    - A layer has no knowledge on higher layers



#### Object Oriented Decomposition

---

- SOLID (Ordering) Principles 
  - Single Responsibility
  - Dependency inversion (Abstraction)
    - Substitution (LSP)
      - FAT Abstraction
        - ISP
  - OCP - Visitor
- Objects
- Concepts[  Ordering ]
  - Encapsulation  - SRP
    - Cohesion 
    - Coupling
  - Reusability
    - Inheritance
    - Uses
      - Association
      - Composition
      - Aggregation
  - Runtime Polymorphism require Inheritance 
    - Abstraction [Loosely Coupled]
  - Dependency Injection
    - Injection By Hand
    - Injection By Container
- Relationship b/w Objects
  - is-a 
  - has-a
- Design Patterns - GOF (Creational / Structural and Behavioral)
- Inheritance V/s Uses
  - Bridge
- Runtime Polymorphism v/s Function pointers (Command Object)
- Why interfaces ?
- Why Abstract Class ?
- is Information Hiding is same as Abstraction
- LOD Violation
- Inheritance v/s enum



#### FinancialRiskCalculation

---

- Information Holders
  - TDSDataModel
  - RDSDataModel
  - RiskConfigParameter
  - RiskInput
  - RiskResult
  - RiskReport
- RiskCalculator
- TDSXMlDataReader
- RDSXMLDataReader
- RiskDataInputGenerator (Merge)
- ExcelExporter
- RiskDataProcessor

