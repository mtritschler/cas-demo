# CAS Demo

This is a PoC to demonstrate the bug described in https://github.com/apereo/cas/pull/4143

Run ``gradle clean run`` and see the application fail eventually with 

    org.springframework.beans.factory.NoUniqueBeanDefinitionException: No qualifying bean of type 
    'org.pac4j.core.context.session.SessionStore<?>' available: expected single matching bean but 
    found 2: oauthDistributedSessionStore,delegatedClientDistributedSessionStore

If one only removes the dependency on `cas-server-support-pac4j-webflow`, the application will also 
fail eventually but much later, which is to be expected since the configuration is incomplete.

If one only removes the dependency on `cas-server-support-oidc`, the application will start just 
fine.