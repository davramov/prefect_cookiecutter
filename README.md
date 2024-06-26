
# Prefect Cookiecutter

In this repository, you will find a Python Cookiecutter template that allows you to run your Python script as a Prefect Flow without having to write additional code. Note that you should have a Prefect server running for this example to work.

## Installation

To begin, make sure you have Prefect and Cookiecutter installed in your Python environment.

    pip show prefect
    pip show cookiecutter

If either are unavailable you can install each manually:

    pip install prefect
    pip install cookiecutter

Or install the dependencies from the included `requirements.txt` file:

    pip install -r requirements.txt

## Example use case
In this example, you will learn how to use this cookiecutter template to create a new project so you can run your code as a Prefect flow.
### Set up the project
To use this template, navigate in your terminal to where you want the new project folder to be created, and run the following command:

    cookiecutter relative/path/to/prefect_cookiecutter

Once you run this, you will be prompted for a few fields (pressing enter will use the default value in parentheses):
 

      [1/5] project_name (prefect_cookiecutter): cookie
      [2/5] project_slug (cookie):     
      [3/5] description (A cookiecutter template for creating a new 
    Prefect project): 
      [4/5] author_name (ALS): 
      [5/5] code_file (code.py): /full/path/to/prefect_cookiecutter/example_code.py

Make sure to copy and enter the full path to the Python file you want to use with this template, such as the example_code.py file included in this repository.

This will create a new folder in the directory you ran  `% cookiecutter prefect_cookiecutter`.

### Prefect Server

You will need a Prefect server running in order to execute the code generated by the Cookiecutter. If you already have a Prefect server running, you can skip this step.

In your terminal, run the following code:

    # Start the Prefect server
    prefect server start

and 

    # Set the Prefect API URL
    prefect config set PREFECT_API_URL=http://127.0.0.1:4200/api

### Run the project

Now that you have run the cookiecutter template and created a new project, you should find a new folder titled with the value you set for `project_name`.

In that folder you should find a file called `flow.py`, which you can run using:

    python flow.py

If everything works, in your terminal you should see a few messages:

    % python flow.py 
	    12:33:15.816 | INFO    | prefect.engine - Created flow run 'enthusiastic-zebra' for flow 'cookie-flow'
	    12:33:15.817 | INFO    | Flow run 'enthusiastic-zebra' - View at https://app.prefect.cloud/account/...
	    12:33:16.325 | INFO    | Flow run 'enthusiastic-zebra' - Created task run 'user_task-0' for task 'user_task'
	    12:33:16.326 | INFO    | Flow run 'enthusiastic-zebra' - Executing 'user_task-0' immediately...
	    Hello, World!
	    12:33:16.946 | INFO    | Task run 'user_task-0' - Finished in state Completed()
	    12:33:17.112 | INFO    | Flow run 'enthusiastic-zebra' - Finished in state Completed('All states completed.')

## Using your script

Now that things are working, you can try using the template on your own Python script by entering the full path of your file when you are prompted for `code_file`, and follow the same steps as above.

**Note:** The project generated by this cookiecutter relies on the full file path for the Python script you would like to run. Because of this, any changes you make to your script will not require rebuilding the cookiecutter template. However, keep in mind that if you move or rename the original script that you reference, the project may no longer work as intended.

If you run into any problems, feel free to submit a Git issue.

