- #Problem: Crosscutting concerns.
- #Goal: better modularization.
	- ##Modularity:
		- Software Decomposition helps in : Changeablility, Independent Development and Comprehensibility. 
		- Separation of Concern Priciple: Grouping and encapsulating part of the system that are related to the same concern into one unit. Edsgr W. Dijkstra
- #Crosscutting Concerns:
	- Concerns that can't be written inside one component in the program. e.g:
		- Logging.
		-  Tracking.
		-  Monitoring.
		- Authentication.
		- Error handling. 
		- Profiling/CAching.
		- **Design patterns**.
		- Syncronization.
	- Code Tangling: Mixing more than one concern together.
	- Code Scattering: Redundant code.
		- Those Affect:
			- Chosion.
			- Readability.
			- Understandability.
			- Maintainability.
			- Reusability.
- #Aspect Oriented Programming:
	-  An extention to OOP, Main driving principle: Separation of Concerns.
- #AspectJ:
	- ##Constructs:
		- Aspect.
		- pointcut:
			- call,execution,get,set,....
		- Advice:
			- after: returning at join point.
			- before: before proceeding at join point.
			- around: on arrival at join point gets explicit control over when&if program proceeds.
			- after returning: a value at join point.
			- after throwing: a throwable at join point.
		- Introduction (inter-type declaration).
	- ##Weaving: a pre-compilation step.
	- ##Crosscutting: 
		- ###Dynamic: Joinpoint concept:
			- define additional behavior to run at certain well-defined points in the execution of the program.
- ##Example:
			public aspect AccountAspect { 				void around(Account account, float amount) : 					call(* Account.withdraw(float)) && 					target(account) && 					args(amount) { 					System.out.println("Before withdrawl of amount: " + amount); 					if(amount > account.getBalance()) 						System.out.println("Cannot make withdrawl"); 					else { 						proceed(account, amount); 						System.out.println("Withdrawl successful, balance: " + account.getBalance()); 					} 				} 			}

	- ###Static:
		- modify the static structure of a program (e.g., adding new methods, implementing new interfaces, modifying the class hierarchy).Add fields, methods, constructors , introduction or inter-type declaration

                declare parents: child (implemnts/extends) super;
                declare (error/warning): case : message;

-	##Local members vs. introduced members
	- ###local: int var;	//lock?
	- ###inter-type declaration: int Class.var;
- ##Policy Enforcement in AspectJ:
	- compile time -> point-cut & run time -> advice enforcement.
	- warning and errors.