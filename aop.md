#### Code Pollution

-----

> Logging , Exception Handling , Validation , Trace , Security ........

```Java
class RiskCalculator{
    ILogger _logger;
    public RiskCalculator(ILogger logger){
        
        this._logger=logger;
    }
    
 public void Calculate(){
     
     this._logger.WriteLogContent("asdffghhj");
 }   
}
interface ILogger{
    void WriteLogContent(string content);
}

class FileLogger:ILogger{
    string filePath;
    public void WriteLogContent(string content){
        
    }
    
}
```



#### AOP 

----

> Separate functional requirement code from non -functional requirement code
>
> Separate Cross Cutting Concerns 
>
> Add Additional Behavior (advice) to existing code  without modifying existing code
>
> AOP frameworks
>
> ​	weaving
>
> - Compile time
>
>   - Metadata Driven - intermediate language based
>
>   - An-notations , custom Attributes
>
>   - Aspect-j, PostSharp
>
>   - Add advice -> private / public 
>
>   - ```
>     [Log()]
>     @Log
>     [Exception]
>     public void Calculate(){
>          
>          
>      }   
>     ```
>
>     
>
> - Runtime 
>
>   - spring AOP
>   - Proxy Pattern + **DI Container** 
>   - Add advice for public interface 
>
> ```Java
> interface IRiskCalculator{
>      void Calculate();
>     
> }
> class LoggerProxyCalculator:IRiskCalculator{
>     IRiskCalculator _actualObject;
>      ILogger _logger;
>     
>    public  LoggerProxyCalculator(IRiskCalculator _calculator,ILogger logger){
>         this._actualObject=_calculator;
>        this._logger=logger;
>     }
>      public void Calculate(){
>      
>      this._logger.WriteLogContent("asdffghhj");
>       this._actualObject.Calculate();
>      this._logger.WriteLogContent("asdffghhj");
>  }  
> }
> class RiskCalculator : IRiskCalculator{
> 
>     
>  public void Calculate(){
>      
> 
>  }   
> }
> 
> interface ILogger{
>     void WriteLogContent(string content);
> }
> 
> class FileLogger:ILogger{
>     string filePath;
>     public void WriteLogContent(string content){
>         
>     }
>     
> }
> IRiskCalculator _obj=DIContainer.GetService<IRiskCalculator>();
> ```
>
> 



TDD

---

- Inside-out (unit of code --> functionalities)