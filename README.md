# Python-exercises
---

### 1.  Create an array of integers, find z-scores and plot
---
Solution: <a href="https://colab.research.google.com/drive/1twgpOZ0oB3RO0f3bhE8ydOc7PKS1zY9-?usp=sharing"> view in Google Colab </a><br>
Plain Code:
*     # import modules
      import numpy as np
      import statistics
      import seaborn as sns
      import warnings
      warnings.filterwarnings("ignore")

      # create a Numpy array containing marks of 15 students
      marks = np.array([150, 180, 145, 130, 120, 185, 110, 135, 165, 144, 166, 153, 132, 170, 148])

      # define a function to calculate Z-score of each marks
      def z_score_calc(input_array):
        u = statistics.mean(input_array)
        sd = statistics.pstdev(input_array)

        z_scores = []

        for X in input_array:
          z_score = (X - u) / sd
          z_scores.append(z_score)

        return z_scores

      # call the function and pass the array of marks as a parameter
      marks_z_scores = z_score_calc(marks)

      # plot the standard normal distribution using 'distplot()' function
      sns.distplot(marks_z_scores)
---
### 2.  Generate a program that accepts only five inputs of integer type from a user and calculate their mean. <br>
##### Hint: *Write multiple functions*.
---
Solution: <a href="https://colab.research.google.com/drive/1YSpANM4FoB8yQbXMJI-CcK-gEayy2mg3?usp=sharing"> view in Google Colab<a><br>
Plain Code:<br>
*     def collect_inputs():
        entry = int(input())
        assert entry >= 0 and entry <= 100
        return entry

      def form_list():
        i=1
        list = []
        while i <= 5:
          try:
            i += 1
            list.append(collect_inputs())
          except ValueError:
            i -= 1
            print("Invalid! Please enter an integer")
          except AssertionError:
            i -= 1
            print("Invalid! Please enter an integer between 0 and 100 inclusive")
        return list

      def mean_list():
        from statistics import mean
        list = form_list()
        average = mean(list)
        print("\nThe average of the list",list,"is",f'{average:.2f}')

      def main():
        print("Please enter 5 integers: \n")
        mean_list()

      main()

