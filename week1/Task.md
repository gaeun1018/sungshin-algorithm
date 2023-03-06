## week1 과제

2. Manually determine the pairs of you who have the same birthday. Explain your method of solution.

     ```
     csv를 읽어와 앞에서부터 시작해 생일이 같은 사람이 있으면 둘을 리스트로 만들어 pair 리스트에 추가한다.
     ```

3. Develop an algorithm for the first question using pseudo code.

    ```
    csv 파일을 연다.
    파일의 각 행에 대해 생일을 비교한다.
      생일이 같고 pair 리스트에 중복된 내용이 없으면 둘을 pair 리스트에 추가한다.
    csv 파일을 닫는다.
    ```
4. Create code that calculates the probability of having at least two students with the same birthday in a class of k students. Apply several different ks.

    ```python
    def cal(k):
      result = 1
      for i in range(1,k+1):
        result *= (365-i+1)/365
      result = 1 - result
      return result
      
    if __name__=="__main__":
      k = int(input("학급 학생 수를 입력하세요."))
      print(cal(k))
    ```


5. Demonstrate that if there are 100 students in a classroom, it is 99.999% probable that there is a pair of students with the same birthday. Conduct computational experiments to solve this problem. 

    a. Describe the algorithm in words as a verbal description.
        
        1에서 100명의 생일이 모두 다를 확률을 뺀다. 
        
        1-(365!/365^k*(365-k)!)

    b. Show its correctness before you do coding. Use inductive proof.
        
        k가 2인 경우 : p = 1 - 365/365 * 364/365 = 0.0027
        k가 23인 경우 : p = 1 - 365/365 * 364/365 * ... * 343/365 = 0.5073
        
        k가 k인 경우 : p = 1 - 365/365 * ... * (365-k+1)/365 = 1 - (365!/365^k*(365-k)!)

    c. Show its efficiency. Use asymptotic notation and explain why.

    d. Construct a pseudo code for your description.

    ```
    csv 파일을 연다.
    파일의 각 행에 대해 생일을 비교한다.
      생일이 같고 pair 리스트에 중복된 내용이 없으면 둘을 pair 리스트에 추가한다.
    csv 파일을 닫는다.
    ```
    e. Develop the code to solve the problem.

    ```python
    def cal(k):
      result = 1
      for i in range(1,k+1):
        result *= (365-i+1)/365
      result = 1 - result
      return result

    if __name__=="__main__":
      k = int(input("학급 학생 수를 입력하세요."))
      print(cal(k))
    ```
    f. Show the results.
    
        0.9999996927510721
6. Apply any resources available to improve your answers and compare your original solution with others. Explain which resources you used and how you employed them.
