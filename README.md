## tailwind class:

    1. animate-spin: to spin anything (div,icon etc)
    2. overflow-x-auto


## Thenology

    1. splash screen 


## Tankstackquery



step-1:                

                            
                import {
                    useQuery,
                } from '@tanstack/react-query'

step-2:

              
                const { data, isLoading, error } = useQuery({
                        queryKey: ['AvailableFood'],
                        queryFn: async () => {
                            const res = await axios.get('https://food-sharing-website-server-beta.vercel.app/Food/available' , {Credentials: true});
                            return res.data;
                        },
                    });
                    
insite main.jsx: 
step:1

                        
                           import {
                            QueryClient,
                            QueryClientProvider,
                            
                            } from '@tanstack/react-query'
step: 2 

                    const queryClient = new QueryClient()
 
 step:3

                        <QueryClientProvider
                        client={queryClient}>
                        </QueryClientProvider>


## axios

# useAxiosSecure Hook:

                     import axios from "axios";

                    export const axiosSecure = axios.create({
                        baseURL : 'http://localhost:5000'
                    })
                    
                    const useAxiosSecure = () => {
                       return axiosSecure;
                    };
                    
                    export default useAxiosSecure;




# post:
                axios.post('https://food-sharing-website-server-beta.vercel.app/MyRequestFoods', data, {
                                            headers: {
                                                "Content-Type": 'Application/json'
                                            }
                                })

                            
# update:
                axios.put(`https://food-sharing-website-server-beta.vercel.app/Food/${food._id}`, data, {
            headers: {
                'content-type': 'application/json'
            }
        })
            .then(response => {
                const responseData = response.data;
                if (responseData.error) {
                    // If there is an error, show SweetAlert2 error message
                    Swal.fire({
                        title: 'Error!',
                        text: responseData.error,
                        icon: 'error',
                        confirmButtonText: 'Ok'
                    });
                } else {
                    // If successful, show success message
                    Swal.fire({
                        title: 'Success!',
                        text: 'Updated successfully',
                        icon: 'success',
                        confirmButtonText: 'Ok'
                    });

                }
            })
            .catch(error => {
                console.error('Error updating tourist spot:', error);
                // If there is an error, show SweetAlert2 error message
                Swal.fire({
                    title: 'Error!',
                    text: 'Failed to update tourist spot. Please try again later.',
                    icon: 'error',
                    confirmButtonText: 'Ok'
                });
            });

# delete:
                const handleDlt = (_id) => {
    Swal.fire({
      title: "Are you sure?",
      text: "You won't be able to revert this!",
      icon: "warning",
      showCancelButton: true,
      confirmButtonColor: "#3085d6",
      cancelButtonColor: "#d33",
      confirmButtonText: "Yes, delete it!"
    }).then((result) => {
      if (result.isConfirmed) {
        axios.delete(`https://food-sharing-website-server-beta.vercel.app/Food/${_id}`)
          .then(response => {
            if (response.data.deletedCount > 0) {
              Swal.fire({
                title: "Deleted!",
                text: "Your Food Item has been deleted.",
                icon: "success",
              });
              const remaining = MyAddedFood.filter(SingleAddedFood => SingleAddedFood._id !== _id);
              setMyAddedFood(remaining);
            } else {
              Swal.fire({
                title: "Error!",
                text: "No item was deleted. It might have already been removed.",
                icon: "error",
              });
            }
          })
          .catch(error => {
            console.error("Error occurred while deleting:", error);
            Swal.fire({
              title: "Error!",
              text: "Failed to delete your Food Item.",
              icon: "error",
            });
          });
      }
    });
  };



  ## useContext :   
   
                    import { createContext } from "react";

                        export const AuthContext = createContext(null)

                        const AuthProvider1 = ( {children} ) => {
                            const values = {
                                name:'kuchu ali',
                                id: '123'
                            }
                            return (
                              <AuthContext.Provider value={values} >{children}</AuthContext.Provider>
                            );
                        };

                        export default AuthProvider1;


## insite Inner Main.jsx file : 

                    <AuthProvider1><AuthProvider1/>

                  
## jakane use korbo:  

                      import { useContext } from 'react'


                      const {name} = useContext(AuthContext)
