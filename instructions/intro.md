# This is the lab guide
Congratulations! If you've gotten this far, you are ready to move on to the
first real exercise! Good luck!

### Opening more Terminals

If you need to open up more terminal windows during the lab, you'll again need
to use the `connect.sh` script to connect to the environment before executing
commands in the exercises:

~~~bash
bash connect.sh {{ISTIO_LAB_HOSTNAME}}
~~~

Then:

~~~bash
sudo -E -i
cd $ISTIO_LAB_HOME
~~~

#### Installing Istio
To install, the Istio operator, execute the following:
~~~bash
oc new-project istio-operator
oc new-project istio-system
oc apply -n istio-operator -f https://raw.githubusercontent.com/Maistra/istio-operator/maistra-0.10/deploy/servicemesh-operator.yaml
~~~

Then wait for the operator to be in the running state:
~~~bash
oc get pods -n istio-operator -l name=istio-operator

NAME                              READY     STATUS    RESTARTS   AGE
istio-operator-5cd6bcf645-fvb57   1/1       Running   0          1h
~~~

Now install the control plane
~~~bash
oc apply -f https://github.com/Maistra/istio-operator/blob/maistra-0.10/deploy/examples/istio_v1alpha3_controlplane_cr_basic.yaml -n istio-system
~~~

In the first lab you'll use Istio to intelligently route traffic. Click **Go To
Next Module** to continue!
