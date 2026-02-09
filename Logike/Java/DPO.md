### Domain Payload Objects (DPOs)

In the third alternative, application services consume and return domain payload objects. A domain payload object is a data transfer object that is aware of the domain model and can contain domain objects. This is essentially a combination of the first two alternatives.

This alternative works best in cases where the domain model is anemic, the aggregates are small and stable, and you want to implement an operation that involves multiple different aggregates. I would say I use DPOs more often as output objects than input objects. However, I try to limit the use of domain objects in DPOs to value objects if only possible.

The advantages of this alternative are:

- You do not need to create DTO classes for everything. You do it when passing a domain object directly to the client is good enough. When you need a custom DTO, you create one. When you need both, you use both.
    

The disadvantages are:

- Same as for the first alternative. The disadvantages can be mitigated by only including immutable value objects inside the DPOs.
Here are two Java examples of using DTOs and DPOs, respectively. The DTO example demonstrates a use case where it makes sense to use a DTO than return the entity directly: Only a fraction of the entity attributes are needed, and we need to include information that does not exist in the entity. The DPO example demonstrates a use case where it makes sense to use a DPO: We need to include many different aggregates that are related to each other in some way.