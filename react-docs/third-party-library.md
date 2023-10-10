We will use some examples to understand how to integrate third-party libraries into React. 

### Integrating bootstrap into React

#### Step 1. Install bootstrap using npm:


```bash
npm install bootstrap
```
or in short, 
```bash
npm i bootstrap
```
If you want to specify a version, you can specify that
```bash
npm i bootstrap@4.6.0
```
By default it is considered as - 
```bash
npm i bootstrap@latest
```

#### Step 2: Including bootstrap css into react project

```javascript
import 'bootstrap/dist/css/bootstrap.min.css';
```
This import can be done in the `main.tsx`, or `main.jsx` file. Since these files are always loaded first, it is a good idea to include the import here.
