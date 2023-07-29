When using the require import method, you can use Next JS dynamic function to lazy load the module like:
```js
import dynamic from "next/dynamic";
const DynamicComp = dynamic() => import('node module');
```