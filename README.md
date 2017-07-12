# Setup an Azure Service Bus Relay

## Add the bin folder to your Web-dir


## Adding extensions

Add the following to the _extensions_ element
```xml

		<extensions>
			<behaviorExtensions>
				<add name="transportClientEndpointBehavior" type="Microsoft.ServiceBus.Configuration.TransportClientEndpointBehaviorElement, Microsoft.ServiceBus, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
			</behaviorExtensions>
			<bindingExtensions>
				<add name="webHttpRelayBinding" type="Microsoft.ServiceBus.Configuration.WebHttpRelayBindingCollectionElement, Microsoft.ServiceBus, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
			</bindingExtensions>

		</extensions>


```

## Adding endpointBehaviors

Add the following inside the _behaviors element

```xml
			<endpointBehaviors>
				<behavior name="sharedSecretClientCredentials">
					<transportClientEndpointBehavior>
						<tokenProvider>
							<sharedAccessSignature keyName=".....keyname...." key=".....key......" />
						</tokenProvider>
					</transportClientEndpointBehavior>
				</behavior>
			</endpointBehaviors>

```


## Adding endpoint inside _service_

NOTE HENRIK: the contract MUST be ITwoWayAsyncVoid if using BizTalk one-way Receive Location!! Otherwise ITwoWayAsync

```xml

				       <endpoint name="RelayEndpoint" address="http://[..yoursbnamespace..].servicebus.windows.net/Predefined/Service1.svc" binding="webHttpRelayBinding" bindingNamespace="http://tempuri.org/" bindingConfiguration="RelayEndpointConfig" behaviorConfiguration="sharedSecretClientCredentials" contract="Microsoft.BizTalk.Adapter.Wcf.Runtime.ITwoWayAsyncVoid" />


```

## Add configuration (security none)

```xml

 <bindings>
      <webHttpRelayBinding>
        <binding name="RelayEndpointConfig">
          <security relayClientAuthenticationType="None" mode="None" />
        </binding>
      </webHttpRelayBinding>
    </bindings>

```

