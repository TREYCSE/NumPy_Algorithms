## Numpy is a library in Python that is primarily used by Data Scientists and Machine Learning Professionals

# Machine Learning Algorithms are equations that we code in Python that allow the Machien to not only make direct commands, but to learn from the information and predict new values; Hence, Artificial Intelligence

# With a simple combination of linear algebra and coding, a machine learning algorithm can predict housing prices

### The code below is an example a Machine Learning Algorithm that I learned that does just that: (I will explain it in the comments:)




# One of the most important things when writing a machine learning algorithm is to reduce the chance of error, to have the most accurate and reliable predictions, this is primarily done usimg the Gradient Descent Formula.
#### In mathematics, this formula has several steps:

        #Function to calculate the cost
        def compute_cost(x, y, w, b):
        
            m = x.shape[0] 
            cost = 0
            
            for i in range(m):
                f_wb = w * x[i] + b
                cost = cost + (f_wb - y[i])**2
            total_cost = 1 / (2 * m) * cost

            return total_cost

#### Now this alone is not going to be enough to plot gradient descent in order to view the local or global minima to be able to predict much

