/**
 * linear_regression.ts
 *
 * Simple gradient descent linear regression.
 *
 * Run:
 *   ts-node src/linear_regression.ts
 */
function linearRegression(x:number[], y:number[], lr=0.01, epochs=1000){
  let m=0,b=0;
  for(let e=0;e<epochs;e++){
    let dm=0, db=0;
    for(let i=0;i<x.length;i++){
      const pred=m*x[i]+b;
      const err=pred-y[i];
      dm+=err*x[i]; db+=err;
    }
    m -= lr*dm/x.length;
    b -= lr*db/x.length;
  }
  return {m,b};
}

(function demo(){
  const xs=[1,2,3,4,5];
  const ys=[2,4,6,8,10];
  const {m,b}=linearRegression(xs,ys,0.01,5000);
  console.log(`Learned line: y=${m.toFixed(2)}x+${b.toFixed(2)}`);
})();
