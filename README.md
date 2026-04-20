while True:
    print("\n--- Student Record Menu ---")
    print("1 - Add Student Record")
    print("2 - View Saved Records")
    print("3 - Exit")
    
    choice = input("Enter your choice: ")
    
    if choice == "1":
       
        name = input("Enter student name: ")
        grade = input("Enter student grade: ")
       
        with open("students.txt", "a") as file:
            file.write(name + "," + grade + "\n")
        print("Record saved successfully.")
        
    elif choice == "2":
       
        try:
            with open("students.txt", "r") as file:
                lines = file.readlines()
                if lines:
                    print("\nSaved Records:")
                    print("-" * 20)
                    for line in lines:
                        parts = line.strip().split(",")
                        if len(parts) == 2:
                            print(f"Name: {parts[0]:<15} Grade: {parts[1]}")
                    print("-" * 20)
                    print(f"Total records: {len(lines)}")
                else:
                    print("No records found yet.")
        except FileNotFoundError:
            print("No records found yet.")
            
    elif choice == "3":
        print("Exiting program... Goodbye!")
        break
    else:
        print("Invalid choice. Please select 1, 2, or 3.")
