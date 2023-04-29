# NumPy!

#### NumPy is a package in Python that is primarily used by Data Scientists and Machine Learning Professionals for Scientific Computing

#### Tools: NumPy, matplotlib
#### Machine Learning Algorithms can either be Supervised (Linear Regression or Classification) or Unsupervised

### These are Examples below of how Linear Regression and Classification in Supervised Learning Works!

1. With a simple combination of linear algebra and coding, a machine learning algorithm can predict housing prices
  ![image](https://i.imgur.com/7IGaWVs.jpg)
2. With Classfication, we can use AI to detect if a patient has cancer!
  ![image](https://i.imgur.com/ljZgdpo.jpg)

# EXAMPLE OF LINEAR REGRESSION
#### One of the most important things when writing a linear regression algorithm is to reduce the chance of error, to have the most accurate and reliable predictions, this is primarily done usimg the Gradient Descent Formula.
#### In mathematics, this formula has several steps:
1. Linear Regression Model (update parameters/guesses w, b)
2. Cost Function J (minimize error of parameters w,b)
3. Gradient Descent Algorithm (repeat until convergence at the global minimum to get the most accurate prediction)

        #Function to calculate the cost
        def compute_cost(x, y, w, b):
        
            m = x.shape[0] 
            cost = 0
            
            for i in range(m):
                f_wb = w * x[i] + b
                cost = cost + (f_wb - y[i])**2
            total_cost = 1 / (2 * m) * cost

            return total_cost

#### Now this alone is not going to be enough to plot gradient descent in order to view the local or global minima to be able to predict any useful output.

        def compute_gradient(x, y, w, b): 
            """
            Computes the gradient for linear regression 
            Args:
            x (ndarray (m,)): Data, m examples 
            y (ndarray (m,)): target values
            w,b (scalar)    : model parameters  
            Returns
            dj_dw (scalar): The gradient of the cost w.r.t. the parameters w
            dj_db (scalar): The gradient of the cost w.r.t. the parameter b     
            """

            
            # Number of training examples
            m = x.shape[0]    
            dj_dw = 0
            dj_db = 0
            
            for i in range(m):  
                f_wb = w * x[i] + b 
                dj_dw_i = (f_wb - y[i]) * x[i] 
                dj_db_i = f_wb - y[i] 
                dj_db += dj_db_i
                dj_dw += dj_dw_i 
            dj_dw = dj_dw / m 
            dj_db = dj_db / m 
                
            return dj_dw, dj_db


        plt_gradients(x_train,y_train, compute_cost, compute_gradient)
        plt.show()

### Now gradient descent is plotted! However, parameters w, b still need to be updated.

