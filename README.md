# Data_Analysis_Python-
Data_Analysis_Python 


##lab 4 part google play diego solucion
#Create a list to hold the 2D data
import csv, matplotlib.pyplot as plt, statistics as stats
import csv
#import library to draw the graphs
import matplotlib.pyplot as plt
import numpy as np
# a).
print()
print("Read the .csv file into python using the CSV library")
import statistics as st



my_file = open("googleplay.csv","r")
# Create a CSV Reader object for my_file
csv_reader = csv.reader(my_file)

# b).
print()
print("Put the .csv file into a suitable 2D list")
# Use the list() function to return the data in the CSV reader as a 2D list
apps = list(csv_reader)


for app in apps[:20]:
    for element in app[:8]:
        #print(members[file][attribute], end=", ")
          print(element, end="\t")
        
        
    print("")
print()
print()


# installed_free = []
# installed_paid = []
for app in apps:
    app[2] = float(app[2])
    app[3] = int(app[3])
    app[5] = int(app[5])
    app[7] = float(app[7])


# for (index, file) in enumerate(members) :
#     members[index][2] = float(file[2])
#     members[index][3] = int(file[3])
#     members[index][5] = int(file[5])
#     members[index][7] = float(file[7])
# print(members)


installed_free = 0
installed_paid = 0

for app in apps:
    
    if app[6] == 'Paid':
        installed_paid += app[5]
    elif app[6] == 'Free':
        installed_free += app[5]
    else:
        print("App is neithee Free nor Paid: ", app)
print(f"Number of installs of free apps: {installed_free:14,}.")
print(f"Number of installs of paid apps: {installed_paid:14,}.")


# is_free = app[6] == "Free"

# if is_free:
#     installed_free.append(file[5])
        
# else:
#     installed_paid.append(file[5])

# print("")
# print("Total number of free:", sum(installed_free))
# print("Total number of paid:", sum(installed_paid))


# g) Show results as pie chart

# plt.bar(['Free', 'Paid'], [(installs_free)/1000000,(installs_Paid)/1000000])
# # plt.ylabel("Installs (millions)")
# plt.show()

# installs = ('Paid', 'Free')

# # start = 0
# stop = len(installs)
# # step = 1
# print(installs)

plt.bar(['Free', 'Paid'], [installed_free, installed_paid])
plt.show()

print("Show the above in a pie chart.")


#g)	Show the above results (from (e)) in a pie chart
# g) Show results as pie chart


plt.pie([int(installed_free), int(installed_paid)], labels=["Free", "Paid"], explode=(0,0.1), shadow=True, autopct='%1.1f%%')
plt.title("Games Installed")
plt.show()

# h).
print("Calculate and display the minimum, maximum and average number of installs for an app.")

# h)
# from statistics as st
from statistics import mean

installs = [app[3] for app in apps]
installed_max = max(installs)
installed_min = min(installs)
installed_avg = int(mean(installs))
print(f"Maximum is", installed_max)
print(f"Minimum  is", installed_min)
print("Average  is", installed_avg)


import matplotlib.pyplot as plt
from statistics import mean


plt.bar(['Maximun','Minimun', 'Average'], [installed_max, installed_min, installed_avg])
plt.title('installs (millions)')
plt.show()



