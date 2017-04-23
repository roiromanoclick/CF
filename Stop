import sys
import time
import boto3

# Enter your instances here: ex. ['X-XXXXXXXX', 'X-XXXXXXXX']
RE_01 = ['i-01444e2930e43dcde', 'i-0188c864d1938ec3e']
RE_02 = ['i-01f4702c200a7b19f', 'i-023eae69b2bfdd9c9']
NS = 'i-04bef4d49f3098d93'
GLV = 'i-04d9ec73e10e9cce3'
DB2 = 'i-068a8b9e53eaf8c92'
DB1 = 'i-07afae68493f825af'
DC = 'i-0fe833ab6158058d5'

ec2 = boto3.resource('ec2')


def lambda_handler(event, context):
    # ec2 = boto3.resource('ec2')
    instances = ec2.instances.filter(
        Filters=[{'Name': 'instance-state-name', 'Values': ['running']}])
    for instance in instances:

        # Check Prod1 Group
        for Prod1 in RE_01:
            if instance.id == Prod1:
                stopInstance(Prod1)
                time.sleep(5)
                # print "***** Stopping PROD 1 Group Completed *****"

                # Check PROD2 status
                # print "***** Checking PROD 2 Group Started *****"
    i = 0
    for instance in instances:

        # Check Prod1 Group
        for Prod2 in RE_02:
            if instance.id == Prod2:
                i = i+1

                # print "***** Checking PROD 2 Group Completed *****"
    k = 0
    if i < 1:
        # print "***** Checking MNG Group Started *****"

        if NS != '':
            stopInstance(NS)
            time.sleep(30)

        if GLV != '':
            stopInstance(GLV)
            time.sleep(30)

        if DB2 != '':
            stopInstance(DB2)
            time.sleep(60)

        if DB1 != '':
            stopInstance(DB1)
            time.sleep(60)

        if DC != '':
            stopInstance(DC)
            time.sleep(60)


def stopInstance(inst):
    print "Stopping the instance "+str(inst)

    try:
        stopInstance = ec2.Instance(inst)
        response = stopInstance.stop()
        # print response



    except Exception, e2:
        error2 = "Error2: %s" % str(e2)
        print(error2)
        sys.exit(0)
