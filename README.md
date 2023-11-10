# calculate the sgpa in gcoea using c++
#include <iostream>
#include <vector>
int calculateGradePoints(int totalMarks) 
{
    if (totalMarks >= 81) 
    {
        return 10;
    } else if (totalMarks >= 73) 
    {
        return 9;
    } else if (totalMarks >= 65) 
    {
        return 8;
    } else if (totalMarks >= 57) 
    {
        return 7;
    } else if (totalMarks >= 49) 
    {
        return 6;
    } else if (totalMarks >= 40) 
    {
        return 5;
    } else 
    {
        return 0;
    }
}
float calculateSubjectSGPA(int mseMarks, int endsemMarks, int taMarks) 
{
    if (endsemMarks >= 20) 
    {
        int totalMarks = mseMarks + endsemMarks + taMarks;
        if (totalMarks >= 40) 
        {
            int gradePoints = calculateGradePoints(totalMarks);
            float sgpa = static_cast<float>(gradePoints);
            return sgpa;
        }
    }
    return 0.0;
}

int main() 
{
    std::vector<std::string> subjects = {"Subject 1", "Subject 2", "Subject 3", "Subject 4", "Subject 5"};
    float totalSGPA = 0.0;
    bool hasBacklog = false;
    for (int i = 0; i < 5; i++) 
    {
        int mseMarks, endsemMarks, taMarks;
        std::cout << "Enter marks for " << subjects[i] << ":\n";
        std::cout << "MSE (out of 30): ";
        std::cin >> mseMarks;
        std::cout << "Endsem (out of 60): ";
        std::cin >> endsemMarks;
        std::cout << "TA (out of 10): ";
        std::cin >> taMarks;
        float subjectSGPA = calculateSubjectSGPA(mseMarks, endsemMarks, taMarks);

        if (subjectSGPA > 0) 
        {
            totalSGPA += subjectSGPA;
        } 
        else 
        {
            std::cout << subjects[i] << " - Sorry, you have a backlog in GCOEA.\n";
            hasBacklog = true;
        }
    }

    if (!hasBacklog) 
    {
        totalSGPA /= 5;
        std::cout << "Total SGPA for all subjects: " << totalSGPA << std::endl;
    } else 
    {
        std::cout << "Since you have a backlog in GCOEA FOR one or more subjects, your SGPA cannot be calculated.\n";
    }

    return 0;
}
