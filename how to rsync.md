>rsync -aPvz -e "ssh -p 2222" source  username@host.com:/destination

source/ skips copying the source directory itself 
source will put source in the destination 

>rsync -aPvz -e "ssh -p 2222" mahabodhi tibetmuseum@157.245.165.83:/storage/www/tibetmuseum.org/wp-content/virtual_tour/

to use the default ssh port
>rsync -aPvz username@host.com:/source ~