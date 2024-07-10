# status-manager
## simple and useful status manager for bulk computations
        Assume that you have multiple folders which each one have a complete and isolated computation task.
        when you need to run them in sequence, may be it waste your time to count the current stage of each one. with this library you can easily handle the progress of each computation inside its folder.    

# Usage
    
    for example assume there are 4 folders inside the working directory, each one has a computation of calculating solar energy of a planet. now you are going to start computation for them which are not finished from previous attempts. I mean something like this:
    ```
    for i in range(1, 5):
        task = f"task-{i}"
        os.system(f"{task}/run_calculations")
    ```
    by using `status-manager`, it will be very easy!
    see this example:

# Example

    ```
    from status_manager import CheckStatus, StatusType

    s = CheckStatus()

    for i in range(1, 5):
        task = f"task-{i}"
        status = s.check(task)
        if status != Statustype.finished:
            os.system(f"{task}/run_calculations")
            status.write_status(task, StatusType.finished)
    ```