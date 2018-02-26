# cuttingVegetables
Cut arbitrary many vegetables into similar size

### Initialize program with modules, classes and import of data

## Import modules
import sys
#import operator

## Create a class which keep track of the weight and number of cuts made to it
class greensak:                     # Name of the class    
    def __init__(self, weight):     # Define the class and initiate self
        self.weight0 = weight       # Sets initial weight
        self.weightNow = weight     # Weight right now.
        self.nbCuts = 0             # Number of cuts
    
    def cut(self):                  # Function to call to cut
        self.nbCuts +=1             # Update number of cuts with 1.
        self.weightNow = self.weight0 / (self.nbCuts + 1) # Cut the vegetable.
        #print('The weight after {0} cuts is {1}. The original weight was {2}'.format(self.nbCuts, self.weightNow, self.weight0))

#%% Function to find the min and max weight and return its index and value.
def findMinMax():
    global maxWindx
    global minWindx
    
    for i in range(0, N):
        tempW[i] = w[i].weightNow
    maxWindx = max([(v,i) for i,v in enumerate(tempW)])
    minWindx = min([(v,i) for i,v in enumerate(tempW)])
    return minWindx, maxWindx

#%% Function to sum number of cuts
def sumNbCuts():
    global sumofCuts
    sumofCuts = 0
        
    for j in range(0, N):
        sumofCuts = sumofCuts + w[j].nbCuts
    return sumofCuts

#%% Function to create predefined list of n size.
def zeroListMaker(n):
    listofzeros = [0] * n
    return listofzeros

#%% ### Import data
#dataRaw = sys.stdin()        # Import data from stdin to array data.
#dataRaw = open('vegetables3.in', 'r')   
#firstRow = dataRaw.readline()
firstRow = sys.stdin.readline()
firstList = firstRow.split()
T = float(firstList[0])                 # Store ratio T (minWeight / maxWeight)
N = int(firstList[1])                   # Store number N vegetables.
#dataF = []                             # Initialize lists
w = []                                  # Array of greensaks; w[0].weight0 = 2000.0

tempW = zeroListMaker(N)
#maxWindx = ()
#minWindx = ()

#for line in dataRaw:                    # Go through lines
for line in sys.stdin: 
    dataStr = line.split()              # Split string into list
        
    for k in range(0, N):               # Convert list of strings into list of float from 0 to N-1.
        #dataF.append(float(dataStr[k])) # Old, dont need this.
        w.append(greensak(float(dataStr[k]))) # Create greensaks in the array w.

#dataRaw.close()


#%% Cut N vegetables
findMinMax()
Ttest = minWindx[0] / maxWindx[0]
while (Ttest < T): # Run this until Ttest satisfies the criteria.
# if Ttest < T
    # Cut biggest piece
    w[maxWindx[1]].cut()
    findMinMax()
    Ttest = minWindx[0] / maxWindx[0]

else:
    # Break loop command.
    sumNbCuts()
    print(sumofCuts)
    
#%% Codeblock, will not run further then here.

# a0 = greensak(1400.0)
# a1 = greensak(1000.0)
