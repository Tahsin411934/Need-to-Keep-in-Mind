## tailwind class:

    1. animate-spin: to spin anything (div,icon etc)
    2. overflow-x-auto


## Thenology

    1. splash screen 


## Tankstackquery

 const { data, isLoading, error } = useQuery({
        queryKey: ['AvailableFood'],
        queryFn: async () => {
            const res = await fetch('https://food-sharing-website-server-beta.vercel.app/Food/available' , {Credentials: true});
            return res.json();
        },
    });

## axios

 axios.post('https://food-sharing-website-server-beta.vercel.app/MyRequestFoods', data, {
            headers: {
                "Content-Type": 'Application/json'
            }
        })
    
