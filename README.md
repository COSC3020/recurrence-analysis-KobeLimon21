# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```
 



This function contains three for loops. 
The first for loop runs for n^2 iterations, as n*n is n^2. 

The second for loop runs for n iterations as it is only n.

The third for loop runs for n^2 iterations, similar to the first loop where it runs n^2 for each iteration in the middle loop of n. 

When multiplying all these: (n^2 * n^2 * n) this gives us a final complexity of n^5.

The recurrence relation I derived was 3T(n/3)+ n^5

3(3T(n/3/3) + (n/3)^5 + n^5

9T(n/9) + (n/3)^5  + n^5

Substituting i in.

$$
T(n) = 3^i T\left(\frac{n}{3^i}\right) + \left( \sum_{j=0}^{i-1} \frac{n}{3^5} \right) n^5
$$



Substituting i for 

3^i T (n/3^i)  + 2n^5

$$
i = \log_3(n)
$$

$$
3^{\log_3(n)} T\left(\frac{n}{3^{\log_3(n)}}\right) + 2n^5
$$

first term simplifies down to n, and n/n is equal to 1 which leaves us with n + 2n^5. 

2n^5 is the highest term, we ignore the constant so n^5 is what we are left with 


 T (n) ∈ O(n^5 ) 




"I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice."

Sources:

Used Chat GPT to generate the summation notation and equation under as I did not grasp it from the website under. 











Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.
