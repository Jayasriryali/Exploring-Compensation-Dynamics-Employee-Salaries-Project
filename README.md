# Exploring-Compensation-Dynamics-Employee-Salaries-Project
 Delving into the intricacies of employee salaries across industries and regions
• Welcome to the Employee Salaries for Different Job Roles Dataset! This dataset
provides valuable insights into the compensation and job roles of employees
across various industries and regions.

• Whether you're an HR analyst, data scientist, or someone interested in
understanding salary trends, this dataset offers a wealth of information to
explore and analyze.

• We encourage you to explore the data, perform insightful analyses, and share
your findings with the Kaggle community. If you find any interesting patterns or
make significant discoveries,

attach(ds_salaries_xl_org)
View(ds_salaries_xl_org)

#to view col names in thee data
names(ds_salaries_xl_org)

#summary statistics-- for numerical data
summary(work_year)

summary(salary)

summary(salary_in_usd)

summary(remote_ratio)

summary(company_size)

#Exploratory Data Analysis
#Data Visualisation


#Salary Distribution Across experience_level

frequency <-table(experience_level)
frequency

x=table(frequency)*100
percentage <- round(relative_frequency)
?barplot
barplot(frequency,names.arg =c("EN","EX","MI","SE"),legend.text = frequency,col = c("pink","skyblue","green","red"),main = "SALARY DISTRIBUTION ACROSS EXPERIENCE LEVEL",xlab ="Experience Level",ylab="salary",las=1,ylim = c(0,650),bty="n")

#Salary Distribution across employement type

frequency1<-table(employment_type)
frequency1
relative_frequency1<-(frequency1/607)*100
relative_frequency1
x=table(frequency1)*100
percentage <- round(relative_frequency)
barplot(relative_frequency1,names.arg = c("CT","FL","FT","PT"),legend.text = round(relative_frequency),col=c("pink","beige","skyblue","brown"),main="SALARY DISTRIBUTION ACROSS EMPLOYMENT TYPE",xlab="Employment type",ylab="salary",las=1,ylim=c(0,100),bty="n")

# Installing packages for scatter plot

install.packages("ggplot2")
library("ggplot2")

table(remote_ratio)
plot(remote_ratio,salary, 
     main = "Remote_ratio vs Salary",
     xlab = "Remote_ratio",
     ylab = "Salary",
     pch = 16, 
     col = "blue")
###

table(company_size)
names(company_size)     
ggplot(ds_salaries_xl_org,aes(x=company_size,y=salary))+geom_point(colors="darkgreen",size=3)+labs(title = "Relation between company size and salary",x="company_size",y="salary")+theme_bw()


##Visual trends in remote work percentages and company sizes

###Impact of remote_ratio on salary
frequency2<-table(remote_ratio)
frequency2
relative_frequency2<-(frequency2/607)*100
relative_frequency2
x=prop.table(frequency2)*100
percentage<-round(relative_frequency2)
barplot(relative_frequency2,names.arg = c("0","50","100"),legend.text =round(relative_frequency2),col = c("beige","lightblue","violet"),main="Impact of remote_ratio on salary",xlab = "RemoteRatio %",ylab="Salary",las=1,ylim=c(0,100))


## impact of comapany size on salary
frequency3<-table(company_size)
frequency3
relative_frequency3<-(frequency3/607)*100
relative_frequency3
x=prop.table(frequency3)*100
percentage<-round(relative_frequency3)
barplot(relative_frequency3,names.arg = c("L","M","S"),legend.text =round(relative_frequency3),col = c("beige","lightblue","violet"),main="Impact of COMPANY_SIZE on salary",xlab = "size of the company",ylab="Salary",las=1,ylim=c(0,100))
 
#FEATURE ENGINEEERING_ CALCULATING AVERAGE SALARY FOR EACH JOB TITLE
#average salary for each job role

average_salary <- aggregate(salary ~ job_title, data = ds_salaries_xl_org, FUN = mean)
print(average_salary)

#FEATURE ENGINEEERING_ CALCULATING AVERAGE SALARY PER EXPERIENCE LEVEL
average_salary_exp <- aggregate(salary ~ experience_level, data = ds_salaries_xl_org, FUN = mean)
print(average_salary_exp)



