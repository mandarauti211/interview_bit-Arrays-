
/**
 * @input A : Read only ( DON'T MODIFY ) 2D integer array ' * @input n11 : Integer array's ( A ) rows
 * @input n12 : Integer array's ( A ) columns
 * 
 * @Output Integer array. You need to malloc memory for result array, and fill result's length in length_of_array
 */
 int* spiralOrder(const int** A, int n11, int n12, int *length_of_array) {
     *length_of_array = n11 * n12; // length of result array
     int *result = (int *) malloc(*length_of_array * sizeof(int));
     // DO STUFF HERE
      
     int i, k = 0, l = 0;
     int m = n11;
     int n = n12;
     int len = 0;
  
     /*  k - starting row index
         m - ending row index
         l - starting column index
         n - ending column index
         i - iterator
     */
     
     while (k < m && l < n)
     {
         /* Print the first row from the remaining rows */
         for (i = l; i < n; ++i)
         {
             //printf("%d ", A[k][i]);
             *(result + len) = A[k][i];
             len++;
         }
         k++;
  
         /* Print the last column from the remaining columns */
         for (i = k; i < m; ++i)
         {
             *(result+len) = A[i][n-1];
             len++;
         }
         n--;
  
         /* Print the last row from the remaining rows */
         if ( k < m)
         {
             for (i = n-1; i >= l; --i)
             {
                 *(result+len) = A[m-1][i];
                 len++;
             }
             m--;
         }
  
         /* Print the first column from the remaining columns */
         if (l < n)
         {
             for (i = m-1; i >= k; --i)
             {
                 *(result+len) = A[i][l];
                 len++;
             }
             l++;    
         }        
     }
   return result;
 }
