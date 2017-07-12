# Setup an Azure Service Bus Relay

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

