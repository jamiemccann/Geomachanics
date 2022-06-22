from numpy.linalg import eig
import matplotlib.pyplot as plt
from matplotlib.patches import Circle


class Stress_Matrix:
    def __init__(self, matrix):
        self.matrix = matrix

    def eigen_numbers(self):
        return eig(self.matrix)

    def eigenvalues(self):
        return eig(self.matrix)[0]

    def eigenvectors(self):
        return eig(self.matrix)[1]

    def StressDiagram(self):
        fig = plt.figure()

        sigma1_eigenvectors = [i[0] for i in self.eigenvectors()]
        sigma2_eigenvectors = [i[1] for i in self.eigenvectors()]
    
        ax = fig.add_axes([0,0,1,1])

        ax.set_aspect('equal', adjustable='box')
        ax.set_xlim(-1,1)
        ax.set_ylim(-1,1)
        ax.scatter(0,0,color =  'black')
        ax.plot([0,sigma1_eigenvectors[0]], [0,sigma1_eigenvectors[1]], 'r')
        ax.plot([0,sigma2_eigenvectors[0]], [0,sigma1_eigenvectors[1]], 'b')
        ax.set_title('Stress Diagram')

    def MohrDiagram(self):
        fig = plt.figure()


        #define principal stresses
        sigma1 = eig(self.matrix)[0].max()
        sigma2 = eig(self.matrix)[0].min()
        #define stress matrix
        sigmaxx = [i[0] for i in self.matrix]
        sigmayy = [i[1] for i in self.matrix]



        ax = fig.add_axes([0,0,1,1])
        ax.set_title('Mohr Diagram')
        ax.set_xlabel('Normal Stress (MPa)', labelpad=100)
        ax.set_ylabel('Shear Stress (Mpa)')
        ax.spines['bottom'].set_position('zero')

        ax.set_aspect('equal', adjustable='box')
        ax.set_xlim(0,80)
        ax.set_ylim(-40,40)
        

        #plot principal stresses
        ax.scatter(sigma1, 0, color = 'r')
        ax.scatter(sigma2, 0, color = 'r')

        #plot matrix stresses and strains
        ax.scatter(sigmaxx[0], -(sigmaxx[1]))
        ax.scatter(sigmayy[1], sigmayy[0])


        #get values for circle plot
        radius = (sigma1 -sigma2)/2
        centre = [[sigma2 + radius], 0]

        draw_circle = plt.Circle((centre), radius, fill = False)
        ax.add_artist(draw_circle)





      




    

        
