# react-infra

_Note: This is a work-in-progress proposal_

### Example

```jsx
import ReactTFM from 'react-terraform'
import { LoadBalancer, Route } from 'react-infra-aws'
import { Environment, Service, Deployment } from 'react-infra'

const ServiceMesh = props => (
  <Environment id={props.env}>
    <Service name="website">
      <Deployment image="nginx" minReplicas={1} maxReplicas={3} />
    </Service>
    <LoadBalancer domain="example.com">
      <Route path="*" to="website" />
    </LoadBalancer>
  </Environment>
)

const env = process.env.TFM_ENV
const outputPath = process.env.TFM_OUTPUT_PATH

ReactTFM.render(outputPath, <ServiceMesh env={env} />)
```
