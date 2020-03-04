# Forelesninger Uke 7

##### Denne uken skal vi se på:
 - Matplotlib, Numpy og Random
 - Feil-håndtering
 

### Matplotlib
Matplotlib er det vanligste bibloteket for å plotte grafer. Får å få tak i Matplotlib åpner vi Terminalen, og skriver

Terminal:

\>\> pip3 install matplotlib


Når pip er ferdig med nedlastning og installering er vi klare til å importere bibloteket


```python
import matplotlib.pyplot as plt # importerer matplotlib med plt som instanse
import numpy as np # numpy er et bibliotek for svært effektiv for lister og databehandling
```


```python
print(dir(np)) # sjekker hva som ligger bibloteket numpy
```

    ['ALLOW_THREADS', 'AxisError', 'BUFSIZE', 'CLIP', 'ComplexWarning', 'DataSource', 'ERR_CALL', 'ERR_DEFAULT', 'ERR_IGNORE', 'ERR_LOG', 'ERR_PRINT', 'ERR_RAISE', 'ERR_WARN', 'FLOATING_POINT_SUPPORT', 'FPE_DIVIDEBYZERO', 'FPE_INVALID', 'FPE_OVERFLOW', 'FPE_UNDERFLOW', 'False_', 'Inf', 'Infinity', 'MAXDIMS', 'MAY_SHARE_BOUNDS', 'MAY_SHARE_EXACT', 'MachAr', 'ModuleDeprecationWarning', 'NAN', 'NINF', 'NZERO', 'NaN', 'PINF', 'PZERO', 'RAISE', 'RankWarning', 'SHIFT_DIVIDEBYZERO', 'SHIFT_INVALID', 'SHIFT_OVERFLOW', 'SHIFT_UNDERFLOW', 'ScalarType', 'Tester', 'TooHardError', 'True_', 'UFUNC_BUFSIZE_DEFAULT', 'UFUNC_PYVALS_NAME', 'VisibleDeprecationWarning', 'WRAP', '_NoValue', '_UFUNC_API', '__NUMPY_SETUP__', '__all__', '__builtins__', '__cached__', '__config__', '__doc__', '__file__', '__git_revision__', '__loader__', '__mkl_version__', '__name__', '__package__', '__path__', '__spec__', '__version__', '_add_newdoc_ufunc', '_arg', '_distributor_init', '_globals', '_mat', '_mklinit', '_pytesttester', 'abs', 'absolute', 'absolute_import', 'add', 'add_docstring', 'add_newdoc', 'add_newdoc_ufunc', 'alen', 'all', 'allclose', 'alltrue', 'amax', 'amin', 'angle', 'any', 'append', 'apply_along_axis', 'apply_over_axes', 'arange', 'arccos', 'arccosh', 'arcsin', 'arcsinh', 'arctan', 'arctan2', 'arctanh', 'argmax', 'argmin', 'argpartition', 'argsort', 'argwhere', 'around', 'array', 'array2string', 'array_equal', 'array_equiv', 'array_repr', 'array_split', 'array_str', 'asanyarray', 'asarray', 'asarray_chkfinite', 'ascontiguousarray', 'asfarray', 'asfortranarray', 'asmatrix', 'asscalar', 'atleast_1d', 'atleast_2d', 'atleast_3d', 'average', 'bartlett', 'base_repr', 'binary_repr', 'bincount', 'bitwise_and', 'bitwise_not', 'bitwise_or', 'bitwise_xor', 'blackman', 'block', 'bmat', 'bool', 'bool8', 'bool_', 'broadcast', 'broadcast_arrays', 'broadcast_to', 'busday_count', 'busday_offset', 'busdaycalendar', 'byte', 'byte_bounds', 'bytes0', 'bytes_', 'c_', 'can_cast', 'cast', 'cbrt', 'cdouble', 'ceil', 'cfloat', 'char', 'character', 'chararray', 'choose', 'clip', 'clongdouble', 'clongfloat', 'column_stack', 'common_type', 'compare_chararrays', 'compat', 'complex', 'complex128', 'complex64', 'complex_', 'complexfloating', 'compress', 'concatenate', 'conj', 'conjugate', 'convolve', 'copy', 'copysign', 'copyto', 'core', 'corrcoef', 'correlate', 'cos', 'cosh', 'count_nonzero', 'cov', 'cross', 'csingle', 'ctypeslib', 'cumprod', 'cumproduct', 'cumsum', 'datetime64', 'datetime_as_string', 'datetime_data', 'deg2rad', 'degrees', 'delete', 'deprecate', 'deprecate_with_doc', 'diag', 'diag_indices', 'diag_indices_from', 'diagflat', 'diagonal', 'diff', 'digitize', 'disp', 'divide', 'division', 'divmod', 'dot', 'double', 'dsplit', 'dstack', 'dtype', 'e', 'ediff1d', 'einsum', 'einsum_path', 'emath', 'empty', 'empty_like', 'equal', 'errstate', 'euler_gamma', 'exp', 'exp2', 'expand_dims', 'expm1', 'extract', 'eye', 'fabs', 'fastCopyAndTranspose', 'fft', 'fill_diagonal', 'find_common_type', 'finfo', 'fix', 'flatiter', 'flatnonzero', 'flexible', 'flip', 'fliplr', 'flipud', 'float', 'float16', 'float32', 'float64', 'float_', 'float_power', 'floating', 'floor', 'floor_divide', 'fmax', 'fmin', 'fmod', 'format_float_positional', 'format_float_scientific', 'format_parser', 'frexp', 'frombuffer', 'fromfile', 'fromfunction', 'fromiter', 'frompyfunc', 'fromregex', 'fromstring', 'full', 'full_like', 'fv', 'gcd', 'generic', 'genfromtxt', 'geomspace', 'get_array_wrap', 'get_include', 'get_printoptions', 'getbufsize', 'geterr', 'geterrcall', 'geterrobj', 'gradient', 'greater', 'greater_equal', 'half', 'hamming', 'hanning', 'heaviside', 'histogram', 'histogram2d', 'histogram_bin_edges', 'histogramdd', 'hsplit', 'hstack', 'hypot', 'i0', 'identity', 'iinfo', 'imag', 'in1d', 'index_exp', 'indices', 'inexact', 'inf', 'info', 'infty', 'inner', 'insert', 'int', 'int0', 'int16', 'int32', 'int64', 'int8', 'int_', 'int_asbuffer', 'intc', 'integer', 'interp', 'intersect1d', 'intp', 'invert', 'ipmt', 'irr', 'is_busday', 'isclose', 'iscomplex', 'iscomplexobj', 'isfinite', 'isfortran', 'isin', 'isinf', 'isnan', 'isnat', 'isneginf', 'isposinf', 'isreal', 'isrealobj', 'isscalar', 'issctype', 'issubclass_', 'issubdtype', 'issubsctype', 'iterable', 'ix_', 'kaiser', 'kron', 'lcm', 'ldexp', 'left_shift', 'less', 'less_equal', 'lexsort', 'lib', 'linalg', 'linspace', 'little_endian', 'load', 'loads', 'loadtxt', 'log', 'log10', 'log1p', 'log2', 'logaddexp', 'logaddexp2', 'logical_and', 'logical_not', 'logical_or', 'logical_xor', 'logspace', 'long', 'longcomplex', 'longdouble', 'longfloat', 'longlong', 'lookfor', 'ma', 'mafromtxt', 'mask_indices', 'mat', 'math', 'matmul', 'matrix', 'matrixlib', 'max', 'maximum', 'maximum_sctype', 'may_share_memory', 'mean', 'median', 'memmap', 'meshgrid', 'mgrid', 'min', 'min_scalar_type', 'minimum', 'mintypecode', 'mirr', 'mod', 'modf', 'moveaxis', 'msort', 'multiply', 'nan', 'nan_to_num', 'nanargmax', 'nanargmin', 'nancumprod', 'nancumsum', 'nanmax', 'nanmean', 'nanmedian', 'nanmin', 'nanpercentile', 'nanprod', 'nanquantile', 'nanstd', 'nansum', 'nanvar', 'nbytes', 'ndarray', 'ndenumerate', 'ndfromtxt', 'ndim', 'ndindex', 'nditer', 'negative', 'nested_iters', 'newaxis', 'nextafter', 'nonzero', 'not_equal', 'nper', 'npv', 'numarray', 'number', 'obj2sctype', 'object', 'object0', 'object_', 'ogrid', 'oldnumeric', 'ones', 'ones_like', 'outer', 'packbits', 'pad', 'partition', 'percentile', 'pi', 'piecewise', 'place', 'pmt', 'poly', 'poly1d', 'polyadd', 'polyder', 'polydiv', 'polyfit', 'polyint', 'polymul', 'polynomial', 'polysub', 'polyval', 'positive', 'power', 'ppmt', 'print_function', 'printoptions', 'prod', 'product', 'promote_types', 'ptp', 'put', 'put_along_axis', 'putmask', 'pv', 'quantile', 'r_', 'rad2deg', 'radians', 'random', 'rank', 'rate', 'ravel', 'ravel_multi_index', 'real', 'real_if_close', 'rec', 'recarray', 'recfromcsv', 'recfromtxt', 'reciprocal', 'record', 'remainder', 'repeat', 'require', 'reshape', 'resize', 'result_type', 'right_shift', 'rint', 'roll', 'rollaxis', 'roots', 'rot90', 'round', 'round_', 'row_stack', 's_', 'safe_eval', 'save', 'savetxt', 'savez', 'savez_compressed', 'sctype2char', 'sctypeDict', 'sctypeNA', 'sctypes', 'searchsorted', 'select', 'set_numeric_ops', 'set_printoptions', 'set_string_function', 'setbufsize', 'setdiff1d', 'seterr', 'seterrcall', 'seterrobj', 'setxor1d', 'shape', 'shares_memory', 'short', 'show_config', 'sign', 'signbit', 'signedinteger', 'sin', 'sinc', 'single', 'singlecomplex', 'sinh', 'size', 'sometrue', 'sort', 'sort_complex', 'source', 'spacing', 'split', 'sqrt', 'square', 'squeeze', 'stack', 'std', 'str', 'str0', 'str_', 'string_', 'subtract', 'sum', 'swapaxes', 'sys', 'take', 'take_along_axis', 'tan', 'tanh', 'tensordot', 'test', 'testing', 'tile', 'timedelta64', 'trace', 'tracemalloc_domain', 'transpose', 'trapz', 'tri', 'tril', 'tril_indices', 'tril_indices_from', 'trim_zeros', 'triu', 'triu_indices', 'triu_indices_from', 'true_divide', 'trunc', 'typeDict', 'typeNA', 'typecodes', 'typename', 'ubyte', 'ufunc', 'uint', 'uint0', 'uint16', 'uint32', 'uint64', 'uint8', 'uintc', 'uintp', 'ulonglong', 'unicode', 'unicode_', 'union1d', 'unique', 'unpackbits', 'unravel_index', 'unsignedinteger', 'unwrap', 'ushort', 'vander', 'var', 'vdot', 'vectorize', 'version', 'void', 'void0', 'vsplit', 'vstack', 'warnings', 'where', 'who', 'zeros', 'zeros_like']
    


```python
print(dir(np.random)) # sjekker hva som ligger numpy.random
```

    ['Lock', 'RandomState', '__RandomState_ctor', '__all__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__path__', '__spec__', 'absolute_import', 'beta', 'binomial', 'bytes', 'chisquare', 'choice', 'dirichlet', 'division', 'exponential', 'f', 'gamma', 'geometric', 'get_state', 'gumbel', 'hypergeometric', 'laplace', 'logistic', 'lognormal', 'logseries', 'mtrand', 'multinomial', 'multivariate_normal', 'negative_binomial', 'noncentral_chisquare', 'noncentral_f', 'normal', 'np', 'operator', 'pareto', 'permutation', 'poisson', 'power', 'print_function', 'rand', 'randint', 'randn', 'random', 'random_integers', 'random_sample', 'ranf', 'rayleigh', 'sample', 'seed', 'set_state', 'shuffle', 'standard_cauchy', 'standard_exponential', 'standard_gamma', 'standard_normal', 'standard_t', 'test', 'triangular', 'uniform', 'vonmises', 'wald', 'warnings', 'weibull', 'zipf']
    

Nå har vi verktøyene vi trenger for å lage vårt første plot. Starter med lage en liste med 'tilfeldige' verdier ved hjelp av


```python
y_values = np.random.uniform(0, 100, 20) # lager en liste med 20 'tilfeldige' flyttall i ønsket intervall
print(y_values) 
```

    [67.75795729 41.21867359 51.82944823 34.37846495 11.07802519  2.09837056
     17.6653909  40.94368712 40.03710324 53.50920474 51.92000073 85.37536986
      6.4533181  37.13948444 57.7281383  73.95597544 15.42600973  7.36099392
     82.68136076 32.77084538]
    


```python
y_values = np.sort(y_values) # sorterer listen
print(y_values)
```

    [ 2.09837056  6.4533181   7.36099392 11.07802519 15.42600973 17.6653909
     32.77084538 34.37846495 37.13948444 40.03710324 40.94368712 41.21867359
     51.82944823 51.92000073 53.50920474 57.7281383  67.75795729 73.95597544
     82.68136076 85.37536986]
    


```python
x_values = np.linspace(0, 100, 20) # lager en liste med 20 uniformt fordelte verdier i intervallet 0 til 100
print(x_values)
```

    [  0.           5.26315789  10.52631579  15.78947368  21.05263158
      26.31578947  31.57894737  36.84210526  42.10526316  47.36842105
      52.63157895  57.89473684  63.15789474  68.42105263  73.68421053
      78.94736842  84.21052632  89.47368421  94.73684211 100.        ]
    

Vi har nå produsert dataen vi trenger for å kunne lage vårt første plot


```python
plt.title('Vårt første plott!') # Tittel på plott

plt.plot(x_values, y_values) # første argument er x-verdier, og andre argument er x-verdier
plt.xlabel('x') # label til x-akse
plt.ylabel('Tilfeldige verdier')# label til y-akse
plt.show()
```


![png](output_10_0.png)


La oss produsere enda liste med tilfeldige verdier, og plotte denne opp denne mot verdiene vi allerede har plottet


```python
y_values2 = np.random.uniform(0, 50, 20) 
y_values2 = np.sort(y_values2) 
```


```python
plt.title('Vårt første plott!')
plt.plot(x_values, y_values)
plt.plot(x_values, y_values2)
plt.xlabel('x')
plt.ylabel('Tilfeldige verdier')
plt.legend(['Random(x) in (0, 100)', 'Random(x) in (0, 20)']) # lager label. Matcher opp nummerering i listen med rekkefølgen plottet var laget
plt.show() # denne funksjonen sikrer at grafene blir plottet i samme vindu
```


![png](output_13_0.png)


Vi kan også lage subplots, men her kan det lønne seg å gjøre dette på en mer objektorientert måte. Enkelt forklart fungerer metoden på følgende måte:

 - subplot oppretter et objekt for plotting, der fig og (ax1, ax2) lagres til objektet. 
 - subplots inputs bestemmer dimmensjonene til et nested liste med objekter. Der objektene er aksene til plottene. Enkeltelementene i listen (ax1, ax2) er lagret henholdsvis til ax1 og ax2.


```python
fig, (ax1, ax2) = plt.subplots(nrows=2, ncols=1) #nrows=ant.rader med akse-objekter, ncols=ant.kolonner med akse-objekter  
print((ax1,ax2))
print(ax1)
print(ax2)
```

    (<matplotlib.axes._subplots.AxesSubplot object at 0x0000022282541C88>, <matplotlib.axes._subplots.AxesSubplot object at 0x0000022282582148>)
    AxesSubplot(0.125,0.536818;0.775x0.343182)
    AxesSubplot(0.125,0.125;0.775x0.343182)
    


![png](output_15_1.png)


 - Videre fordeler vi plottene til hvert enkeltelement i listen med objekter.
 - Hele figuren blir lagret til fig



```python
fig, (ax1, ax2) = plt.subplots(nrows=2, ncols=1)


ax1.plot(x_values, y_values) 
ax1.legend(['Random(x) in (0, 100)'])
ax1.set_xlabel('x') # Vi må endre funksjonene til set_
ax1.set_ylabel('Tilfeldige verdier')


ax2.plot(x_values, y_values2, '--') 
ax2.legend(['Random(x) in (0, 20)'])
ax2.set_ylabel('Tilfeldige verdier')
ax2.set_xlabel('x') # Vi må endre funksjonene til set_


plt.show() 
```


![png](output_17_0.png)


### Animasjoner med Matplotlib

###### eksempel: 'CPU_percent_monitor.py' 
Vi skal lage et live-plott som monitorier hvor prosent av CPU-en vi bruker.


```python
import psutil 
```


```python
print(dir(psutil)) # sjekker hva som ligger i psutil
```

    ['ABOVE_NORMAL_PRIORITY_CLASS', 'AF_LINK', 'AIX', 'AccessDenied', 'BELOW_NORMAL_PRIORITY_CLASS', 'BSD', 'CONN_CLOSE', 'CONN_CLOSE_WAIT', 'CONN_CLOSING', 'CONN_DELETE_TCB', 'CONN_ESTABLISHED', 'CONN_FIN_WAIT1', 'CONN_FIN_WAIT2', 'CONN_LAST_ACK', 'CONN_LISTEN', 'CONN_NONE', 'CONN_SYN_RECV', 'CONN_SYN_SENT', 'CONN_TIME_WAIT', 'Error', 'FREEBSD', 'HIGH_PRIORITY_CLASS', 'IDLE_PRIORITY_CLASS', 'IOPRIO_HIGH', 'IOPRIO_LOW', 'IOPRIO_NORMAL', 'IOPRIO_VERYLOW', 'LINUX', 'MACOS', 'NETBSD', 'NIC_DUPLEX_FULL', 'NIC_DUPLEX_HALF', 'NIC_DUPLEX_UNKNOWN', 'NORMAL_PRIORITY_CLASS', 'NoSuchProcess', 'OPENBSD', 'OSX', 'POSIX', 'POWER_TIME_UNKNOWN', 'POWER_TIME_UNLIMITED', 'Popen', 'Process', 'REALTIME_PRIORITY_CLASS', 'STATUS_DEAD', 'STATUS_DISK_SLEEP', 'STATUS_IDLE', 'STATUS_LOCKED', 'STATUS_PARKED', 'STATUS_RUNNING', 'STATUS_SLEEPING', 'STATUS_STOPPED', 'STATUS_TRACING_STOP', 'STATUS_WAITING', 'STATUS_WAKING', 'STATUS_ZOMBIE', 'SUNOS', 'TimeoutExpired', 'WINDOWS', 'ZombieProcess', '_LOWEST_PID', '_PY3', '_TOTAL_PHYMEM', '__all__', '__author__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__path__', '__spec__', '__version__', '_as_dict_attrnames', '_assert_pid_not_reused', '_common', '_compat', '_cpu_busy_time', '_cpu_times_deltas', '_cpu_tot_time', '_last_cpu_times', '_last_cpu_times_2', '_last_per_cpu_times', '_last_per_cpu_times_2', '_lock', '_pmap', '_ppid_map', '_pprint_secs', '_psplatform', '_psutil_windows', '_pswindows', '_timer', '_wrap_numbers', 'boot_time', 'collections', 'contextlib', 'cpu_count', 'cpu_freq', 'cpu_percent', 'cpu_stats', 'cpu_times', 'cpu_times_percent', 'datetime', 'disk_io_counters', 'disk_partitions', 'disk_usage', 'errno', 'functools', 'getloadavg', 'long', 'net_connections', 'net_if_addrs', 'net_if_stats', 'net_io_counters', 'os', 'pid_exists', 'pids', 'process_iter', 'pwd', 'sensors_battery', 'signal', 'subprocess', 'swap_memory', 'sys', 'test', 'threading', 'time', 'users', 'version_info', 'virtual_memory', 'wait_procs', 'win_service_get', 'win_service_iter']
    


```python
print(psutil.cpu_times_percent()) # sjekker hva som funksjonen returnerer
```

    scputimes(user=9.1, system=5.3, idle=84.9, interrupt=0.6, dpc=0.1)
    


```python
print((psutil.cpu_times_percent()[0]))
```

    6.2
    

Vi ser at første output er hva vi ser etter. Vi kan begynne å gjøre klar animasjonen


```python
from itertools import count
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation
plt.style.available # Viser oss liste over forskjellige stiler for plott
plt.style.use('seaborn-dark-palette') # stil for plot
import time
import psutil

time_cpu = []
cpu_percent = []

index = count()

def animate(i):
    #abstime.sleep(1)
    time_cpu.append(next(index))
    cpu_percent.append((psutil.cpu_times_percent()[0]))
    plt.cla()
    plt.plot(time_cpu, cpu_percent)

ani = FuncAnimation(plt.gcf(), animate, interval=1000)

plt.show()


```


    <Figure size 432x288 with 0 Axes>

