 ```mermaid
    classDiagram
        
        class LegalEntity {
            Registration date : Date
            Legal name : String
            Alternative name : String
        }

        LegalEntity "0..1" --> "0..*" SignatoryRights : Signatory rights

        class SignatoryRights {
            Description : String
        }

        SignatoryRights "*" --> "*" Post : mandates
        SignatoryRights "*" --> "*" SignatoryRule : mandatesJointly

        class SignatoryRule {
            Description : String
        }

        SignatoryRule --> Post : oneOf
        SignatoryRule --> Post : anyOf
        SignatoryRule --> Post : allOf

        class Post {

        }

        Post --> Person : Held by
        Post --> Role : Role

        class Role {
            Preferred label : String
            Notation : String
        }

        class Person {
            Name : String
            Birthdate : Date
        }


```