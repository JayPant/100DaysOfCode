
```java

/*Complete the function below*/
class GfG {
    public Stack<Integer> sort(Stack<Integer> s) {
        // add code here.
        Stack<Integer> helper = new Stack<>();
        
        while(!s.isEmpty()){
            
            int temp = s.pop();
            
            while(!helper.isEmpty() && helper.peek() < temp ){
                s.push(helper.pop());
            }
            
            helper.push(temp);
        }
        
        while(!helper.isEmpty()){
            s.push(helper.pop());
        }
        
        return s;
    }
}
```