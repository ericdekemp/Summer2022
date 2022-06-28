# Convert list of lattitude and longitude into utm cooridnates, both as '.csv'
# Data must be set up as follows, with headers:
#   Points, Latitude, Longitude,
#   1,lat1,long1,
#   2,lat2,long2,
#   ...,...,...,
#==============================================================================
# Provide input file
iFile = '../SanAndreasFaultTrace_latLong.csv'
print('File to read: %s' % (iFile))

# Provide output file
oFile = '../SanAndreasFaultTrace_UTM.csv'
print('File to be created: %s' % (oFile))
#==============================================================================
import numpy as np
import utm

# Read the data from the lat & long file
data = np.genfromtxt(iFile, delimiter=',',skip_header=1)
data= data[~np.isnan(data).any(axis=1)]
point = data[:,0]
lat = data[:,1]
lon = data[:,2]

# Write new .csv file with the UTM Northings and Eastings
nFile = open(oFile, 'w')
nFile.write('Point, Easting, Northing\n' )

# Fill the UTM array
for i in range(len(point)):
    nFile.write('%f, ' % (point[i]))
    utmData = utm.from_latlon(lat[i],lon[i])
    nFile.write('%f, %f' % (utmData[0],utmData[1]))
    if i != len(point):
        nFile.write('\n')
nFile.close()
#==============================================================================
