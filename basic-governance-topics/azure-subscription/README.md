# Azure Subscription

As stated earlier, when creating an Azure subscription an AAD tenant is automatically created for you. With this, after creating and/or synchronizing users in Azure Active Directory, you can now allow your users to subscribe to your subscription and its existing resources.

According with the size of your cloud environment, you can also create additional subscriptions or [associate other existing subscriptions](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) with your Azure Active Directory tenant. Having at least two subscriptions, one for the production environment and the other for non-production ones, is a good practice for segregation of the environment and for [scalability](https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/scale-subscriptions).

An important point to be considered is about permissioning is that there are two types of functions/attributions that are distinct but totally related to each other:

1. [Azure Roles](https://docs.microsoft.com/en-us/azure/role-based-access-control/rbac-and-directory-admin-roles#azure-roles): Azure Roles use [Role Based Access Control (RBAC)](https://docs.microsoft.com/en-us/azure/role-based-access-control/overview) and are granted in the context of Azure resources within a subscription. There are three basic roles of Owner, Collaborator and Reader. In addition to them there are more than 70 other roles that are more related to services specifically, [here you can see the list with all](https://docs.microsoft.com/en-us/azure/role-based-access-control/built-in-roles). In addition to the native functions, you may want to create your own [custom roles](https://docs.microsoft.com/en-us/azure/role-based-access-control/custom-roles) and maximize the type of control you want to apply.
2. [Azure Active Directory roles](https://docs.microsoft.com/en-us/azure/role-based-access-control/rbac-and-directory-admin-roles#azure-ad-roles): Azure Active Directory roles are used exclusively for the management of Azure Active Directory resources.

This image can help you understand a little about how the functions of Azure and Azure Active Directory are related:

![](../../.gitbook/assets/ad-rbac-roles.png)

An Azure subscription has a trust relationship with the AAD to authenticate and authorize users, services and devices.

It is important to know that the same AAD tenant can have multiple subscriptions trusting him, but each signature can only confirm on a single AAD tenant. It means that you can have the same user base on the AAD tenant for different subscriptions.

A subscription is a logical container for your resources and each resource is associated with only one signature. They are directly related to billing and payment.

The data in the subscriptions remains for a while after being canceled, and the subscriptions themselves are usually visible, even after being canceled in the Portal and in the APIs. There is information about the cancellation process in the [documentation available here](https://docs.microsoft.com/en-us/azure/cost-management-billing/manage/cancel-azure-subscription).

A subscription serves different purposes because it is a legal contract, a payment contract, a scaling limit and, an administrative limit. All details are [described in this link](https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/ready/considerations/fundamental-concepts#azure-subscription-purposes).

It is important to define an architecture for the use of subscriptions that there is a better organization and management of resources, especially on the segregation of permission and control of [existing limits on subscriptions](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits). To help with this, there is a documented [decision guide](https://docs.microsoft.com/en-us/azure/cloud-adoption-framework/decision-guides/subscriptions/) that is super interesting to understanging the best way to model your organization and define subscription design strategies.

