# Nordic Smart Government Signatory Rights Model

The model describes Signatory Rights as an collection of Signatory Rules that defines required combination of agents (Person/Legal entity) holding a position (Post) in an organisation (Legal entity). Agent can hold one to many positions in an organisation and can acquire signatory power trough multiple signatory rules.

```mermaid
 %%{init:{'flowchart':{'nodeSpacing': 30, 'rankSpacing': 95, 'htmlLabels': false}}}%%
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

        %%SignatoryRights "0..*" --> "*" Post : mandates
        SignatoryRights "0..*" --> "*" SignatoryRule : defines

        class SignatoryRule {
            Description : String
        }

        SignatoryRule ..> Post : (one to five)Of
        SignatoryRule --> Post : majorityOf
        SignatoryRule --> Post : allOf

        class Post {

        }

        Post --> Agent : Held by
        Post --> Role : Role

        class Role {
            Preferred label : String
            Notation : String
        }

        class Agent {
            Name : String
        }

```

## Legal entity

A self-employed person, company, or organization that has legal rights and obligations. Class reused from [Core business vocabulary](https://semiceu.github.io/Core-Business-Vocabulary/releases/2.1.0/#Agent).

## Signatory rights

Describes mandate that gives power to agent(s) to represent a legal entity alone or jointly trough a post(s) in a legal entity. Signatory rights can be defined as free text or structured as machine readable signatory rules.

## Signatory rule

Structured rules that dictate the combination of posts, roles and agents to whom the representation power is granted. Rules can be used to structure signatory rights that can be granted alone to an individual agent or jointly for group of agents. The rule is interpreted jointly if it points to multiple posts using restriction properties. 

## Post

A Post represents some position within an organization that exists independently of the agent or agents filling it. A post can be held by multiple persons or legal entities. The Post concept is reused from the [W3C Organization ontology](https://www.w3.org/TR/vocab-org/#class-post).

## Restriction properties

Signatory rights are commonly granted to an agent or a group of agents trough a post and a role in an organisation. The rights can be granted to an agent acting alone or jointly with another agents. Typically these type of rules have been described as freeform text which can be structured using following classification:

* One of
* Two of
* Three of
* Four of
* Five of
* Majority of
* All of

Restrictions one to five, majority and all of are modelled as properties (instead of separate class) to simplify the model. Restriction properties are used by Signatory rules to constraint the number of agents needed to form a group that can hold the signatory power.

## Agent

Entity that is able to carry out action. Class reused from FOAF / [Core business vocabulary](https://semiceu.github.io/Core-Business-Vocabulary/releases/2.1.0/#Agent).

## Role
 
 Denotes a role that a Person or other Agent can take in an organization. Class reused from [Organisation ontology](https://www.w3.org/TR/vocab-org/#class-role).

 TBD!

 NSG&B defines set of roles to be used as classification.

 # Examples

 TBD!
 
 Some text examples and point to RDF examples. TBD!