# react route v6 syntax

// Routes can use as the alternative of Switch

```jsx
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";
<Router>
	<li>
			<Link to="/your-route-name">this is the route link</Link>
	</li>
	<Routes>
	  <Route path="/your-route-name" element={<YourComponent />} />
  </Routes>
</Router>
```

simply put’s all the route addresses in the <Route /> this will target that component on the path. the path is linked to the link wherever you want connect your component just add the link with the route address.