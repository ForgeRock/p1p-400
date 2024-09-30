# PingOne Protect 400: Data Analysis and Configuration of Protect Integrations

The links in this document are to the product documentation and will assist in configuring the integrations in your deployment. The following links are to major sections of the documentation related to PingOne Protect:

* [Threat Protection using PingOne Protect](https://docs.pingidentity.com/pingone/threat_protection_using_pingone_protect/p1_protect_overview.html)  
  * [Protect dashboard](https://docs.pingidentity.com/pingone/threat_protection_using_pingone_protect/p1_protect_dashboard.html)  
  * [Risk evaluations](https://docs.pingidentity.com/pingone/threat_protection_using_pingone_protect/p1_protect_risk_evaluations.html)  
  * [Predictors](https://docs.pingidentity.com/pingone/threat_protection_using_pingone_protect/p1_protect_risk_predictors.html)  
    * [Adding custom predictors](https://docs.pingidentity.com/pingone/threat_protection_using_pingone_protect/p1_protect_adding_custom_predictors.html)  
    * [Adding composite predictors](https://docs.pingidentity.com/pingone/threat_protection_using_pingone_protect/p1_protect_adding_composite_predictors.html)  
  * [Risk policies](https://docs.pingidentity.com/pingone/threat_protection_using_pingone_protect/p1_protect_risk_policies.html)  
  * [Protect related alerts](https://docs.pingidentity.com/pingone/monitoring/p1_alerts.html)
    * Suspicious Traffic
    * Data Quality Issue  
* [PingOne Protect Integration Kit](https://docs.pingidentity.com/integrations/pingone/pingone_protect_integration_kit/pf_p1_protect_ik.html)  
* [DaVinci PingOne Protect Connector](https://docs.pingidentity.com/connectors/p1_protect_connector.html)  
* [PingAccess integration with PingOne Protect](https://docs.pingidentity.com/pingaccess/latest/agents_and_integrations/pa_p1risk_policy_eval_integration.html)  
* [PingFederate integration with PingOne Protect](https://docs.pingidentity.com/pingfederate/latest/introduction_to_pingfederate/pf_additional_integr.html)

## Configuring PingAccess Integration With PingOne Protect

The key documents for integrating PingAcess with PingOne Protect are listed below in the order that they should be used for the initial configuration of PingAccess:

1. Add a [PingFederate connection](https://docs.pingidentity.com/r/en-us/pingone/p1\_c\_create\_connection\_pf) used by PingAccess:  
   * PingAccess uses the PingFederate connection to connect to the PingOne services for integration with PingOne Protect.  
2. Define a [PingOne Protect policy](https://docs.pingidentity.com/r/en-us/pingone/pingone\_p1risk\_risk\_policies) based on the requirements of your application in PingAccess:  
   * The selected predictors are based on the decision in the [PingAccess policy](https://docs.pingidentity.com/r/en-us/pingaccess-80/pa\_adding\_a\_risk\_policy) to collect or not collect device information using the [PingOne Protect Signals SDK](https://docs.pingidentity.com/r/en-us/pingone/pingone\_c\_risk\_signals\_sdk).  
   * If using the SDK, you can create a [staging policy](https://docs.pingidentity.com/r/en-us/pingone/pingone\_protect\_evaluating\_staging\_policy) to evaluate the impact of not having the predictors that require the SDK.  
3. Connect [PingAccess to PingOne](https://docs.pingidentity.com/r/en-us/pingaccess-80/pa\_adding\_a\_p1\_connection) using the PingOne connection [credentials](https://docs.pingidentity.com/r/en-us/pingone/p1\_add\_credentials).  
4. Define the [rules](https://docs.pingidentity.com/r/en-us/pingaccess-80/pa\_rules) and [authentication challenge policies](https://docs.pingidentity.com/r/en-us/pingaccess-80/pa\_authentication) to be used in your PingAccess risk policy.  
   * Any instructions sent to the token provider; for example, authentication requirements or prompt parameters should be handled by the token provider. In the case of PingFederate, this may require adjustments to the [authentication](https://docs.pingidentity.com/r/en-us/pingfederate-121/pingfed-authenticationpolicies) policies.  
5. Define your PingAccess [risk policy](https://docs.pingidentity.com/r/en-us/pingaccess-80/pa\_adding\_a\_risk\_policy) or policies:  
   * During a learning period, you may simply allow requests through and then apply the rules and challenge policies after the learning period.  
6. Link risk policy to the [application(s) and resources](https://docs.pingidentity.com/r/en-us/pingaccess-80/pa\_applications\_operations) of protected web applications.

## Configuring PingFederate Integration With PingOne Protect

The key documents for integrating PingFederate with PingOne Protect are listed below in the order that they should be used for the initial configuration of PingFederate:

1. Add a [PingFederate connection](https://docs.pingidentity.com/r/en-us/pingone/p1\_pf\_connection) used by PingFederate to connect to PingOne services such as PingOne Protect.  
2. Define a [PingOne Protect policy](https://docs.pingidentity.com/r/en-us/pingone/pingone\_p1risk\_risk\_policies) based on the requirements of your application in PingFederate:  
   * You may need more than one policy depending on how you are planning to integrate pingOne Protect into PingFederate.  
   * Consider creating a [staging policy](https://docs.pingidentity.com/r/en-us/pingone/pingone\_protect\_evaluating\_staging\_policy) to evaluate the impact of using different predictors or policy settings.  
3. Connect [PingFederate to PingOne](https://docs.pingidentity.com/r/en-us/pingfederate-121/help\_pingoneconnections\_pingoneconnectioncreate) using the PingOne connection [credentials](https://docs.pingidentity.com/r/en-us/pingone/p1\_add\_credentials).  
4. The latest [PingOne Protect Integration Kit](https://docs.pingidentity.com/r/en-us/pingfederate-pingone-protect-ik/pingfederate\_pingone\_protect\_ik) should be deployed in your PingFederate cluster:   
   * This kit is part of the standard PingFederate download and Docker product images provided by Ping.  
   * An important consideration is the [device profiling methods](https://docs.pingidentity.com/r/en-us/pingfederate-pingone-protect-ik/pingfederate\_pingone\_protect\_ik\_device\_profiling\_methods) available through the SDK; the default PingFederate templates implement the SDK.  
5. Configure one or more [providers](https://docs.pingidentity.com/r/en-us/pingfederate-pingone-protect-ik/pingfederate\_pingone\_protect\_ik\_configuring\_a\_provider\_instance) based on your authentication policy needs.  
6. Configure one or more [PingOne Protect IdP adapters](https://docs.pingidentity.com/r/en-us/pingfederate-pingone-protect-ik/pingfederate\_pingone\_protect\_ik\_configuring\_an\_adapter\_instance) based on your authentication policy needs.  
7. Configure your [Identity First](https://docs.pingidentity.com/r/en-us/pingfederate-121/pf\_config\_identif\_first\_adapt\_instance) and [HTML Form](https://docs.pingidentity.com/r/en-us/pingfederate-pingone-protect-ik/pingfederate\_pingone\_protect\_ik\_configuring\_a\_provider\_instance) adapters to use the PingOne Protect providers:  
   * The form adapter  is covered further down on the provider's page of the link provided.  
8. Add or adjust [authentication policies](https://docs.pingidentity.com/r/en-us/pingfederate-121/pf\_defining\_auth\_policies) to leverage PingOne Protect:  
   * In an initial learning period, you would not take any actions.  
   * Add [rules](https://docs.pingidentity.com/r/en-us/pingfederate-121/pf\_config\_rules\_auth\_policies) and take action after the learning period to handle the [risk levels](https://docs.pingidentity.com/r/en-us/pingfederate-pingone-protect-ik/pingfederate\_pingone\_protect\_ik\_adding\_risk\_level\_results\_to\_your\_authentication\_policy).  
   * For guidance, review the [SSO flow](https://docs.pingidentity.com/r/en-us/pingfederate-pingone-protect-ik/pingfederate\_pingone\_protect\_ik\_overview\_of\_the\_sso\_flow) in the documentation.
